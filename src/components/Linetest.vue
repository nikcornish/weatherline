<script>
import { Bar } from 'vue-chartjs';
export default {
  extends: Bar,
  props: ['chartdata'],
  computed: {
    forecastArray() {
      return this.chartdata.forecast.forecastday;
    },
    location() {
      return this.chartdata.location.name
    },
    temps() {
      return this.forecastArray.map(entry => Math.floor(entry.day.maxtemp_c))
    },
    summaries() {
      return this.forecastArray.map(entry => entry.day.condition.text)
    }
  },
  mounted() {
    this.renderChart({
      labels: this.summaries,
      datasets: [
        { 
          label: this.location, 
          data: this.temps,
          backgroundColor: 'grey',
        }
      ],
    }, {
      responsive: true, 
      maintainAspectRatio: false,
      scales: {
          yAxes: [
            { 
              ticks: {
                beginAtZero: true,
                max: 30
              }
            }
          ]
        }
    })
  }
}
</script>