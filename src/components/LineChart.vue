<script>

	import {Line} from '../plugins/BaseCharts'

	export default {
		extends: Line,
		props: ['id', 'dates', 'closes', 'rotation'],
		mounted() {
			this.renderChart({
				labels: this.dates, //['January', 'February', 'March', 'April', 'May', 'June', 'July'],
				datasets: [
					{
						label: this.id,
						fill: false,
						borderColor: '#833ebe',
						data: this.closes, //[40, 39, 10, 40, 39, 80, 40]
					}
				]
			}, {
				responsive: true, maintainAspectRatio: false,
				legend: {position: 'bottom'}, title: {text: this.id, position: 'top', display: true, fontSize: 16},
				scales: {
					xAxes: [{
						ticks: {
							maxRotation: this.rotation !== undefined ? this.rotation: 45,
							minRotation: this.rotation !== undefined ? this.rotation: 0,
						}
					}]
				}
			})
		}
	}
</script>

<style scoped lang="scss">
  canvas {
    width: 100% !important;
    max-height: 400px;
  }

  #doughnut-chart {
    height: 100% !important;
    width: 100% !important;
    margin: 24px;
  }
</style>
