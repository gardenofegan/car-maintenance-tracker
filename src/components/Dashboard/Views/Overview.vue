<template>
  <div>

    <!--Stats cards-->
    <div class="row">
      <div class="col-lg-3 col-sm-6" v-for="stats in statsCards">
        <stats-card>
          <div class="icon-big text-center" :class="`icon-${stats.type}`" slot="header">
            <i :class="stats.icon"></i>
          </div>
          <div class="numbers" slot="content">
            <p>{{stats.title}}</p>
            {{stats.value}}
          </div>
          <div class="stats" slot="footer">
            <i :class="stats.footerIcon"></i> {{stats.footerText}}
          </div>
        </stats-card>
      </div>
    </div>

    <!--Charts-->
    <div class="row">

      <div class="col-xs-12">
        <chart-card :chart-data="usersChart.data" :chart-options="usersChart.options">
          <h4 class="title" slot="title">Total Cost of Ownership</h4>
          <span slot="subTitle">All Vehicles</span>
          <span slot="footer">
            <i class="ti-reload"></i> Updated 3 minutes ago</span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Sentra
            <i class="fa fa-circle text-warning"></i> Town & Country
            <!-- <i class="fa fa-circle text-warning"></i> Click Second Time -->
          </div>
        </chart-card>
      </div>

      <div class="col-md-6 col-xs-12">
        <chart-card :chart-data="preferencesChart.data" chart-type="Pie">
          <h4 class="title" slot="title">Maintanence Costs by Category</h4>
          <span slot="subTitle"> % of total cost across active vehicles</span>
          <span slot="footer">
            <i class="ti-timer"></i> Last updated 2 days ago</span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Heating & A/C
            <i class="fa fa-circle text-danger"></i> Other
            <i class="fa fa-circle text-warning"></i> Tires
          </div>
        </chart-card>
      </div>

      <div class="col-md-6 col-xs-12">
        <chart-card :chart-data="activityChart.data" :chart-options="activityChart.options" chart-type="Bar">
          <h4 class="title" slot="title">Maintanence by Month</h4>
          <span slot="subTitle"> Across all years</span>
          <span slot="footer">
            <i class="ti-check"></i> Last updated a week ago</span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Sentra
            <i class="fa fa-circle text-warning"></i> Town & Country
          </div>
        </chart-card>
      </div>

    </div>

  </div>
</template>
<script>
  import StatsCard from 'components/UIComponents/Cards/StatsCard.vue'
  import ChartCard from 'components/UIComponents/Cards/ChartCard.vue'
  export default {
    components: {
      StatsCard,
      ChartCard
    },
    /**
     * Chart data used to render stats, charts. Should be replaced with server data
     */
    data () {
      return {
        statsCards: [
          {
            type: 'info',
            icon: 'ti-car',
            title: 'Sentra',
            value: 'Nissan',
            footerText: 'Last update a month ago',
            footerIcon: 'ti-calendar'
          },
          {
            type: 'warning',
            icon: 'ti-car',
            title: 'Town & Country',
            value: 'Chrysler',
            footerText: 'Updated yesterday',
            footerIcon: 'ti-calendar'
          },
          {
            type: 'danger',
            icon: 'ti-plus',
            title: 'Add Vehicle',
            value: ' ',
            footerText: 'Click to add',
            footerIcon: 'ti-timer'
          },
          {
            type: 'danger',
            icon: 'ti-plus',
            title: 'Add Vehicle',
            value: ' ',
            footerText: 'Click to add',
            footerIcon: 'ti-timer'
          }
        ],
        usersChart: {
          data: {
            labels: ['1/2011', '7/2011', '1/2012', '7/2012', '1/2013', '7/2013', '1/2014', '7/2014'],
            series: [
              [10000, 10150, 10225, 10562, 10594, 11626, 12698, 12895, 14952],
              [7000, 7152, 7193, 8240, 8387, 8435, 9535, 9642, 9744]
            ]
          },
          options: {
            low: 0,
            high: 15000,
            showArea: true,
            height: '245px',
            axisX: {
              showGrid: false
            },
            lineSmooth: this.$Chartist.Interpolation.simple({
              divisor: 3
            }),
            showLine: true,
            showPoint: false
          }
        },
        activityChart: {
          data: {
            labels: ['Jan', 'Feb', 'Mar', 'Apr', 'Mai', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
            series: [
              [0, 543, 220, 680, 40, 500, 123, 434, 68, 610, 756, 5],
              [230, 203, 0, 80, 30, 55, 600, 664, 88, 10, 0, 795]
            ]
          },
          options: {
            seriesBarDistance: 7,
            axisX: {
              showGrid: false
            },
            height: '245px'
          }
        },
        preferencesChart: {
          data: {
            labels: ['62%', '32%', '6%'],
            series: [62, 32, 6]
          },
          options: {}
        }

      }
    }
  }

</script>
<style>

</style>
