<template>
  <v-container
    id="wizard"
    tag="section"
  >
    <base-material-wizard
      v-model="tab"
      :available-steps="availableSteps"
      :items="tabs"
      class="mx-auto"
      @click:next="next"
      @click:prev="tab--"
    >
      <v-tab-item class="pb-12">
        <form
          action=""
          data-vv-scope="about"
        >
          <div class="text-center display-1 font-weight-light mb-6">
            Let's start with basic information (with validation)
          </div>

          <v-row
            class="mx-auto"
            justify="space-around"
            style="max-width: 500px;"
          >
            <v-col
              cols="auto"
              class="text-center"
            >
              <input
                ref="file"
                type="file"
                class="d-none"
                @change="onChange"
              >
              <v-card
                :class="image ? 'success--text' : 'grey--text'"
                class="mx-auto mt-0 d-inline-flex v-card--account"
                outlined
                height="106"
                width="106"
                @click="$refs.file.click()"
              >
                <v-img
                  v-if="image"
                  :src="image"
                  height="100%"
                  width="100%"
                />
                <v-icon
                  v-else
                  class="mx-auto"
                  size="96"
                >
                  mdi-account
                </v-icon>
              </v-card>

              <div class="font-weight-bold grey--text">
                CHOOSE PICTURE
              </div>
            </v-col>

            <v-col
              cols="12"
              md="6"
            >
              <v-text-field
                v-model="first"
                v-validate="'required'"
                :error-messages="errors.collect('about.first')"
                color="secondary"
                data-vv-name="first"
                label="First Name*"
                prepend-icon="mdi-face"
                validate-on-blur
              />

              <v-text-field
                v-model="last"
                v-validate="'required'"
                :error-messages="errors.collect('about.last')"
                color="secondary"
                data-vv-name="last"
                label="Last Name*"
                prepend-icon="mdi-account"
                validate-on-blur
              />
            </v-col>

            <v-col cols="12">
              <v-text-field
                v-model="email"
                v-validate="'required'"
                :error-messages="errors.collect('about.email')"
                color="secondary"
                data-vv-name="email"
                label="Email*"
                prepend-icon="mdi-email"
                validate-on-blur
              />
            </v-col>
          </v-row>
        </form>
      </v-tab-item>

      <v-tab-item class="pb-12">
        <form
          action=""
          data-vv-scope="account"
        >
          <v-responsive
            class="mx-auto"

            max-width="500"
          >
            <div class="text-center display-1 grey--text font-weight-light mb-6">
              What are you doing? (checkboxes)
            </div>

            <input
              v-validate="'required'"
              :value="stringAccount"
              type="hidden"
              data-vv-name="type"
            >

            <v-item-group
              v-model="account"
              class="row"
              multiple
            >
              <v-item
                v-for="(account, i) in accounts"
                :key="i"
              >
                <template v-slot="{ active, toggle }">
                  <v-col
                    class="text-center"
                    cols="4"
                  >
                    <v-card
                      :class="active ? 'success--text' : 'grey--text'"
                      class="mb-6 mx-auto pa-10 d-inline-block v-card--account"
                      outlined
                      @click="toggle"
                    >
                      <v-icon
                        large
                        v-text="account.icon"
                      />
                    </v-card>

                    <div
                      class="text-uppercase subtitle-2 text--primary"
                      v-text="account.type"
                    />
                  </v-col>
                </template>
              </v-item>
            </v-item-group>
          </v-responsive>
        </form>
      </v-tab-item>

      <v-tab-item class="pb-12">
        <div class="text-center display-1 grey--text font-weight-light mb-6">
          Are you living in a nice area?
        </div>

        <form
          action=""
          data-vv-scope="address"
        >
          <v-row
            class="mx-auto"
            justify="space-around"
            style="max-width: 500px;"
          >
            <v-col
              cols="12"
              md="8"
            >
              <v-text-field
                v-model="address"
                v-validate="'required'"
                :error-messages="errors.collect('address.address')"
                color="secondary"
                data-vv-name="address"
                label="Street Name*"
                validate-on-blur
              />
            </v-col>

            <v-col
              cols="12"
              md="4"
            >
              <v-text-field
                v-model="street"
                v-validate="'required'"
                :error-messages="errors.collect('address.street')"
                color="secondary"
                data-vv-name="street"
                label="Street Number*"
                validate-on-blur
              />
            </v-col>

            <v-col
              cols="12"
              md="6"
            >
              <v-text-field
                v-model="city"
                v-validate="'required'"
                :error-messages="errors.collect('address.city')"
                color="secondary"
                data-vv-name="city"
                label="City*"
                validate-on-blur
              />
            </v-col>

            <v-col
              cols="12"
              md="6"
            >
              <v-autocomplete
                v-model="state"
                v-validate="'required'"
                :autocomplete="Date.now()"
                :error-messages="errors.collect('address.state')"
                :items="states"
                color="secondary"
                data-vv-name="state"
                label="State*"
                validate-on-blur
              />
            </v-col>
          </v-row>
        </form>
      </v-tab-item>
    </base-material-wizard>
  </v-container>
</template>

<script>
  export default {
    name: 'DashboardFormsWizard',

    data: () => ({
      account: [],
      accounts: [
        {
          icon: 'mdi-pencil',
          type: 'design'
        },
        {
          icon: 'mdi-code-tags',
          type: 'code'
        },
        {
          icon: 'mdi-laptop',
          type: 'develop'
        }
      ],
      address: '',
      city: '',
      email: '',
      first: '',
      image: null,
      last: '',
      state: '',
      states: [
        'Alabama', 'Alaska', 'American Samoa', 'Arizona',
        'Arkansas', 'California', 'Colorado', 'Connecticut',
        'Delaware', 'District of Columbia', 'Federated States of Micronesia',
        'Florida', 'Georgia', 'Guam', 'Hawaii', 'Idaho',
        'Illinois', 'Indiana', 'Iowa', 'Kansas', 'Kentucky',
        'Louisiana', 'Maine', 'Marshall Islands', 'Maryland',
        'Massachusetts', 'Michigan', 'Minnesota', 'Mississippi',
        'Missouri', 'Montana', 'Nebraska', 'Nevada',
        'New Hampshire', 'New Jersey', 'New Mexico', 'New York',
        'North Carolina', 'North Dakota', 'Northern Mariana Islands', 'Ohio',
        'Oklahoma', 'Oregon', 'Palau', 'Pennsylvania', 'Puerto Rico',
        'Rhode Island', 'South Carolina', 'South Dakota', 'Tennessee',
        'Texas', 'Utah', 'Vermont', 'Virgin Island', 'Virginia',
        'Washington', 'West Virginia', 'Wisconsin', 'Wyoming'
      ],
      street: '',
      tab: 0,
      tabs: ['About', 'Account', 'Address']
    }),

    computed: {
      stringAccount () {
        return this.account.join(',')
      },
      scope () {
        if (this.tab === 0) return 'about'
        else if (this.tab === 2) return 'address'
        return 'account'
      },
      availableSteps () {
        const steps = [0]

        if (
          this.first &&
          this.last &&
          this.email
        ) steps.push(1)

        if (this.stringAccount && steps.includes(1)) steps.push(2)

        if (
          this.address &&
          this.street &&
          this.city &&
          this.state &&
          steps.includes(2)
        ) steps.push(3)

        return steps
      }
    },

    methods: {
      next () {
        this.validateForm(this.scope).then(item => {
          if (!item) return

          if (this.tab === this.tabs.length - 1) {
            alert('Form finished')
          } else {
            this.tab++
          }
        })
      },
      onChange (val) {
        const value = val.target.files[0]

        if (!value) return (this.image = null)

        this.image = URL.createObjectURL(value)
      },
      validateForm (scope) {
        return this.$validator.validateAll(scope)
      }
    }
  }
</script>

<style lang="sass">
  .v-card.v-card.v-card--account
    border-color: currentColor
    border-width: 4px

    .v-icon
      color: inherit

  .v-card--account,
  .v-card--account:before
    border-radius: 50%

</style>
