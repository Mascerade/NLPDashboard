<template>
  <div>
    <line-chart :chart-data="dataCollection" :options="chartOptions"></line-chart>
  </div>
</template>

<script>
import LineChart from './LineChart.js'

export default {
  props: ['title', 'data', 'labels', 'yLabel', 'xLabel'],
  components: {
    LineChart
  },
  data () {
    return {
      chartOptions: {
        maintainAspectRatio: false,
        scales: {
          yAxes: [{
            scaleLabel: {
              display: true,
              labelString: this.yLabel
            }
          }],
          xAxes: [{
            scaleLabel: {
              display: true,
              labelString: this.xLabel
            }
          }]
        }
      }
    }
  },
  computed: {
    dataCollection () {
      return {
        labels: this.labels,
        datasets: [
          {
            data: this.data,
            label: this.title,
            tension: 0,
            backgroundColor: 'rgba(4, 93, 233, 0.35)',
            borderColor: 'rgba(4, 93, 233, 1)',
            borderWidth: 1
          }
        ]
      }
    }
  }
}
</script>

<style scoped>
  div {
    height: 100%;
  }

</style>
