<template>
  <v-container fluid>
    <v-row>
      <v-col
        cols="12"
        lg="4"
      >
        <base-material-chart-card
          :data="dailySalesChart.data"
          :options="dailySalesChart.options"
          color="success"
          type="Line"
          class="px-4 py-3"
        >
          <h4 class="display-1 font-weight-light mt-2">
            Rounded Line Chart
          </h4>

          <div class="grey--text font-weight-light">
            Line Chart
          </div>
        </base-material-chart-card>
      </v-col>

      <v-col
        cols="12"
        lg="4"
      >
        <base-material-chart-card
          :data="emailsSubscriptionChart.data"
          :options="emailsSubscriptionChart.options"
          :responsive-options="emailsSubscriptionChart.responsiveOptions"
          color="orange darken-1"
          type="Line"
          class="px-4 py-3"
        >
          <h4 class="display-1 font-weight-light mt-2">
            Line Chart With Points
          </h4>

          <div class="grey--text font-weight-light">
            Straight Lines Chart
          </div>
        </base-material-chart-card>
      </v-col>

      <v-col
        cols="12"
        lg="4"
      >
        <base-material-chart-card
          :data="dataCompletedTasksChart.data"
          :options="dataCompletedTasksChart.options"
          color="info"
          type="Bar"
          class="px-4 py-3"
        >
          <h4 class="display-1 font-weight-light mt-2">
            Simple Bar Chart
          </h4>

          <div class="grey--text font-weight-light">
            Last Last Campaign Performance
          </div>
        </base-material-chart-card>
      </v-col>

      <v-col
        cols="12"
        lg="6"
      >
        <base-material-card
          id="coloured-line"
          color="info"
          icon="mdi-chart-timeline-variant"
          class="px-4 py-3"
        >
          <template v-slot:after-heading>
            <div class="display-1 mt-2 font-weight-light">
              Coloured Line Chart
              <span class="subtitle-1">— Rounded</span>
            </div>
          </template>

          <chartist
            :data="colouredLine.data"
            :options="colouredLine.options"
            type="Line"
            style="max-height: 150px;"
            class="mt-3"
          />
        </base-material-card>
        <div class="py-3" />
        <base-material-card
          id="coloured-line"
          color="warning"
          icon="mdi-chart-timeline-variant"
          class="px-4 py-3"
        >
          <template v-slot:after-heading>
            <div class="display-1 font-weight-light mt-2">
              Coloured Line Chart
              <span class="subtitle-1">— Multiple</span>
            </div>
          </template>

          <chartist
            :data="multipleLine.data"
            :options="multipleLine.options"
            type="Line"
            style="max-height: 150px;"
            class="mt-3"
          />
        </base-material-card>
      </v-col>

      <v-col
        cols="12"
        lg="6"
      >
        <base-material-card
          id="multiple-bar"
          color="success"
          icon="mdi-poll-box"
          class="px-4 py-3"
        >
          <template v-slot:after-heading>
            <div class="display-1 mt-2 font-weight-light">
              Multiple Bars Chart
              <span class="subtitle-1">— Bar Chart</span>
            </div>
          </template>

          <chartist
            :data="multipleBar.data"
            :options="multipleBar.options"
            type="Bar"
            style="max-height: 150px;"
            class="mt-3"
          />
        </base-material-card>
        <div class="py-3" />

        <base-material-card
          id="pie"
          color="success"
          icon="mdi-chart-pie"
          title="Pie Chart"
          class="px-4 py-3"
        >
          <chartist
            :data="pie.data"
            :options="pie.options"
            type="Pie"
            style="max-height: 250px;"
          />

          <v-divider class="ma-3" />

          <div class="px-3">
            <div class="body-2 text-uppercase grey--text font-weight-bold mb-3">
              Legend
            </div>

            <v-row
              align="center"
              class="ma-0"
            >
              <v-avatar
                class="mr-1"
                color="info"
                size="12"
              />

              <span class="mr-3 font-weight-light">Apple</span>

              <v-avatar
                class="mr-1"
                color="warning"
                size="12"
              />

              <span class="mr-3 font-weight-light">Samsung</span>

              <v-avatar
                class="mr-1"
                color="red"
                size="12"
              />

              <span class="mr-3 font-weight-light">Windows Phone</span>
            </v-row>
          </div>
        </base-material-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        colouredLine: {
          data: {
            labels: ["'06", "'07", "'08", "'09", "'10", "'11", "'12", "'13", "'14", "'15"],
            series: [
              [275, 500, 290, 55, 700, 700, 500, 750, 630, 900, 930]
            ]
          },
          options: {
            low: 0,
            high: 1000, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
            chartPadding: {
              top: 0,
              right: 0,
              bottom: 0,
              left: 0
            }
          }
        },
        dailySalesChart: {
          data: {
            labels: ['M', 'T', 'W', 'T', 'F', 'S', 'S'],
            series: [
              [12, 17, 7, 17, 23, 18, 38]
            ]
          },
          options: {
            low: 0,
            high: 50, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
            chartPadding: {
              top: 0,
              right: 0,
              bottom: 0,
              left: 0
            },
            showPoint: false
          }
        },
        dataCompletedTasksChart: {
          data: {
            labels: ['12am', '3pm', '6pm', '9pm', '12pm', '3am', '6am', '9am'],
            series: [
              [230, 750, 450, 300, 280, 240, 200, 190]
            ]
          },
          options: {
            low: 0,
            high: 1000, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
            chartPadding: {
              top: 0,
              right: 0,
              bottom: 0,
              left: 0
            }
          }
        },
        emailsSubscriptionChart: {
          data: {
            labels: ['Ja', 'Fe', 'Ma', 'Ap', 'Mai', 'Ju', 'Jul', 'Au', 'Se', 'Oc', 'No', 'De'],
            series: [
              [542, 443, 320, 780, 553, 453, 326, 434, 568, 610, 756, 895]

            ]
          },
          options: {
            lineSmooth: this.$chartist.Interpolation.none(),
            axisX: {
              showGrid: false
            },
            low: 0,
            high: 1000,
            chartPadding: {
              top: 0,
              right: 5,
              bottom: 0,
              left: 0
            }
          },
          responsiveOptions: [
            ['screen and (max-width: 640px)', {
              seriesBarDistance: 5,
              axisX: {
                labelInterpolationFnc(value) {
                  return value[0]
                }
              }
            }]
          ]
        },
        multipleBar: {
          data: {
            labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
            series: [
              [542, 443, 320, 780, 553, 453, 326, 434, 568, 610, 756, 895],
              [400, 200, 250, 575, 450, 300, 285, 370, 370, 410, 620, 690]
            ]
          },
          options: {
            seriesBarDistance: 10,
            lineSmooth: this.$chartist.Interpolation.none(),
            axisX: {
              showGrid: false
            },
            low: 0,
            high: 900,
            chartPadding: {
              top: 0,
              right: 5,
              bottom: 0,
              left: 0
            }
          },
          responsiveOptions: [
            ['screen and (max-width: 640px)', {
              seriesBarDistance: 5,
              axisX: {
                labelInterpolationFnc(value) {
                  return value[0]
                }
              }
            }]
          ]
        },
        multipleLine: {
          data: {
            labels: ["'06", "'07", "'08", "'09", "'10", "'11", "'12", "'13", "'14", "'15"],
            series: [
              [275, 500, 290, 55, 700, 700, 500, 750, 630, 900, 930],
              [575, 600, 490, 75, 300, 400, 700, 450, 130, 200, 330],
              [575, 300, 890, 155, 640, 540, 800, 250, 230, 400, 630]
            ]
          },
          options: {
            low: 0,
            high: 1000, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
            chartPadding: {
              top: 0,
              right: 0,
              bottom: 0,
              left: 0
            }
          }
        },
        pie: {
          data: {
            series: [62, 32, 6]
          },
          options: {
            labelInterpolationFnc: (value) => `${value}%`
          }
        },
        headers: [
          {
            sortable: false,
            text: 'ID',
            value: 'id'
          },
          {
            sortable: false,
            text: 'Name',
            value: 'name'
          },
          {
            sortable: false,
            text: 'Salary',
            value: 'salary',
            align: 'right'
          },
          {
            sortable: false,
            text: 'Country',
            value: 'country',
            align: 'right'
          },
          {
            sortable: false,
            text: 'City',
            value: 'city',
            align: 'right'
          }
        ],
        items: [
          {
            id: 1,
            name: 'Dakota Rice',
            country: 'Niger',
            city: 'Oud-Tunrhout',
            salary: '$35,738'
          },
          {
            id: 2,
            name: 'Minerva Hooper',
            country: 'Curaçao',
            city: 'Sinaai-Waas',
            salary: '$23,738'
          },
          {
            id: 3,
            name: 'Sage Rodriguez',
            country: 'Netherlands',
            city: 'Overland Park',
            salary: '$56,142'
          },
          {
            id: 4,
            name: 'Philip Chanley',
            country: 'Korea, South',
            city: 'Gloucester',
            salary: '$38,735'
          },
          {
            id: 5,
            name: 'Doris Greene',
            country: 'Malawi',
            city: 'Feldkirchen in Kārnten',
            salary: '$63,542'
          }
        ],
        tabs: 0,
        list: {
          0: false,
          1: false,
          2: false
        }
      }
    },
    methods: {
      complete(index) {
        this.list[index] = !this.list[index]
      }
    }
  }
</script>

<style lang="sass">
  #coloured-line
    .ct-series-a .ct-line,
    .ct-series-a .ct-point
      stroke: #00cae3 !important

  #multiple-bar
    .ct-series-a .ct-bar
      stroke: #00cae3 !important

    .ct-series-b .ct-bar
      stroke: #f44336 !important

  #pie
    .ct-series-a .ct-slice-pie
      fill: #00cae3 !important

    .ct-series-b .ct-slice-pie
      fill: #f44336 !important
</style>
