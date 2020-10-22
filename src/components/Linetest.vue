<script>
import { Bar } from 'vue-chartjs';
export default {
  extends: Bar,
  mounted() {
    this.renderChart({
      labels: ['Monday', 'Tuesday', 'Wednesday', 'Thursday'],
      datasets: [
        { 
          label: 'Commits', 
          data: [10, 20, 30, 55], 
          backgroundColor: 'blue',
        }
      ],
    }, {
      responsive: true, 
      maintainAspectRatio: false,
      scales: {
          yAxes: [
            { 
              ticks: {
                beginAtZero: true
              }
            }
          ]
        }
    })
  }
}
</script>