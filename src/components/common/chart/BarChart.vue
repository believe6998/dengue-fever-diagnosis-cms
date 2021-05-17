<script>
import { Bar } from 'vue-chartjs'

export default {
  extends: Bar,
  props: ['statistical'],
  mounted () {
    this.doRenderChart()
  },
  methods: {
    doRenderChart () {
      this.renderChart(
        {
          labels: this.statistical.labels,
          datasets: this.statistical.datasets
        },
        {
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            yAxes: [{
              id: 1,
              position: 'left'
            }, {
              id: 2,
              position: 'right'
            }]
          }
        }
      )
    }
  }
}
</script>
