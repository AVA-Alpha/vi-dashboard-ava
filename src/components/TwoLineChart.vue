<script>

	import {Line} from '../plugins/BaseCharts'

	export default {
		extends: Line,
		props: ['id1', 'id2', 'dates', 'closes1', 'closes2'],
		mounted() {
			this.renderChart({
				labels: this.dates, //['January', 'February', 'March', 'April', 'May', 'June', 'July'],
				datasets: [
					{
						label: this.id1,
						fill: false,
						borderColor: '#833ebe',
						data: this.closes1, //[40, 39, 10, 40, 39, 80, 40]
					},
					{
						label: this.id2,
						fill: false,
						borderColor: '#e079f8',
						data: this.closes2, //[40, 39, 10, 40, 39, 80, 40]
					},
				]
			}, {
				responsive: true,
				maintainAspectRatio: false,
				legend: {position: 'bottom'},
				title: {text: this.id1 + '-' + this.id2, position: 'top', display: true, fontSize: 16}
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
