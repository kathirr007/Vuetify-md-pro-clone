<template>
  <v-container
    id="calendar"
    fluid
    tag="section"
  >
    <base-v-component
      heading="Calendar"
      link="components/calendars"
    />

    <v-row>
      <v-col
        cols="12"
        md="10"
        class="mx-auto"
      >
        <v-card>
          <v-toolbar flat>
            <v-toolbar-title>August 2019</v-toolbar-title>

            <v-spacer />

            <calendar-btn
              v-for="(t, i) in types"
              :key="i"
              @click="type = t"
            >
              {{ t }}
            </calendar-btn>

            <v-spacer />

            <calendar-btn @click="$refs.calendar.prev()">
              <v-icon>mdi-chevron-left</v-icon>
            </calendar-btn>

            <calendar-btn @click="$refs.calendar.next()">
              <v-icon>mdi-chevron-right</v-icon>
            </calendar-btn>
          </v-toolbar>

          <v-sheet
            height="600"
            flat
            class="mt-5"
          >
            <v-calendar
              ref="calendar"
              v-model="calendar"
              :events="events"
              :type="type"
              event-color="primary"
              now="2019-01-08"
            />
          </v-sheet>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  // Components
  import { VBtn } from 'vuetify/lib'

  export default {
    name: 'DashboardCalendar',

    components: {
      CalendarBtn: {
        extends: VBtn,

        props: {
          color: {
            type: String,
            default: 'secondary'
          },
          minWidth: {
            type: Number,
            default: 0
          },
          rounded: {
            type: Boolean,
            default: true
          }
        },

        computed: {
          classes() {
            return {
              ...VBtn.options.computed.classes.call(this),
              'mx-1': true,
              'text-lowercase': true
            }
          }
        }
      }
    },

    data: () => ({
      calendar: '2019-01-08',
      disabled: true,
      events: [
        {
          name: 'Vacation',
          start: '2018-12-30',
          end: '2019-01-02'
        },
        {
          name: 'Meeting',
          start: '2019-01-07'
        },
        {
          name: '30th Birthday',
          start: '2019-01-03'
        },
        {
          name: 'New Year',
          start: '2019-01-01'
        },
        {
          name: 'Conference',
          start: '2019-01-21'
        },
        {
          name: 'Hackathon',
          start: '2019-01-30',
          end: '2019-02-01'
        }
      ],
      focus: '',
      type: 'month',
      types: [
        'month',
        'week',
        'day'
      ]
    })
  }
</script>

<style lang="sass">
  #calendar
    .v-calendar-weekly__day:last-child,
    .v-calendar-weekly__head-weekday:last-child
      border-right: none

    .v-calendar-weekly__week:last-child .v-calendar-weekly__day
      border-bottom: none
</style>
