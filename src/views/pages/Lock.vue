<template>
  <v-container
    id="lock"
    fill-height
    tag="section"
  >
    <v-row justify="center">
      <v-slide-y-transition appear>
        <v-card
          class="mt-6 mt-md-0"
          light
          max-width="100%"
          width="250"
        >
          <v-card-text class="text-center">
            <v-avatar
              class="mt-n12 mb-6 elevation-12"
              color="grey"
              size="88"
            >
              <v-img src="https://demos.creative-tim.com/material-dashboard-pro/assets/img/faces/avatar.jpg" />
            </v-avatar>

            <div class="display-2 font-weight-light mb-3 text--darken-2 grey--text">
              Tania Andrew
            </div>

            <v-text-field
              class="mb-8"
              color="secondary"
              label="Enter Password"
            />

            <pages-btn>
              Unlock
            </pages-btn>
          </v-card-text>
        </v-card>
      </v-slide-y-transition>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'PagesLock',

    components: {
      PagesBtn: () => import('./components/Btn')
    }
  }
</script>
