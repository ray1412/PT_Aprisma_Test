<script>
import {Doughnut,mixins} from 'vue-chartjs'
const { reactiveProp } = mixins
export default Doughnut.extend({
	name: 'DoughnutChart',
	mixins: [reactiveProp],
    data () {
      	return {
	        //Chart.js options that controls the appearance of the chart
	        options: {
	        	...Chart.defaults.doughnut,
	        	responsive:true,
            	maintainAspectRatio:true,
	        	// title: {
		        //     display: true,
		        //     text: 'Assets',
		        //     position: 'top'
		        // },
			  	pieceLabel: {
				    render: 'label',
				    fontSize: 14,
				    overlap: true
				 },
		        legend : {
		        	display: false
		        },
		        tooltips: {
		        	enable : true
		        }
	        }
	    }
    },
    mounted () {
    //renderChart function renders the chart with the datacollection and options object.
      this.renderChart(this.chartData, this.options)
    }
  })
</script>

<style lang="css" scoped>
</style>