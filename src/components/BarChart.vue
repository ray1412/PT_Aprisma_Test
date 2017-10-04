<script>
import {Bar,mixins} from 'vue-chartjs'
const { reactiveProp } = mixins
export default Bar.extend({
  name: 'BarChart',
  mixins: [reactiveProp],
   data () {
      	return {
	        //Chart.js options that controls the appearance of the chart
	        options: {
	        	...Chart.defaults.bar,
	        	legend:{
	        		position: 'bottom'
	        	},
	        }
	    }
    },
    mounted () {
    //renderChart function renders the chart with the datacollection and options object.
      this.renderChart(this.chartData, this.options)
    }
});
</script>

<style lang="css" scoped>
</style>