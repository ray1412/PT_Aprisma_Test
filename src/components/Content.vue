<template>
	<v-app class="appDivEdited">
		<div class="header">
			<div class="page-title">Dashboard</div>
			<div class="user-last-login">
				<div class="text">Last Login {{date}}</div>
				<div class="vertical-align-middle"></div>
			</div>
			<v-spacer></v-spacer>
			<div class="user-customised">
				<div class="text">
					<v-icon left class="icon">settings</v-icon>Customize Dashboard
				</div>
				<div class="vertical-align-middle"></div>
			</div>
		</div>
		<div class="content-wrapper">
			<!-- <h2>kiw</h2> -->
			<v-container fluid grid-list-md class="defaultContainer">
				<v-layout row wrap >
					<v-flex d-flex xs12 sm6 md6 class="content-wrapper-left">
						<v-layout row wrap class="hundredWidth">
							<v-flex d-flex class="hundredWidth">
								<div class="content-cards">
									<v-container class="defaultContainer">
										<v-layout row wrap>
											<v-flex xs4 md3>
												<img class="user_logo" src="../assets/img/user_logo.png"/>
												<div class="vertical-align-middle"></div>
											</v-flex>
											<v-flex xs8 md9>
												<div class="general-content name">PT. Aprisma Indonesia</div>
												<div class="general-content user">Welcome,&nbsp;<b>Jeremy Brown</b></div>
												<div class="general-content date">Thursday, February 21, 2014</div>
												<div class="general-content messages"><v-icon left style="color:#5151ff">message</v-icon><span>&nbsp;1 New Messages</span></div>
												<div class="general-content task"><v-icon left style="color:#5151ff">timer</v-icon><span>&nbsp;3 Pending Task</span></div>
											</v-flex>
										</v-layout>
									</v-container>
									<div class="view-more"> View more </div>
								</div>
							</v-flex>
							<v-flex d-flex class="hundredWidth">
								<div class="content-cards">
									<div class="content-subheader">
										<div class="title">Account Overview</div>
										<div class="close">X</div>
										<div class="clearfix"></div>
									</div>
									<div class="ao-container">
										<v-layout row wrap class="hundredWidth">
											<v-flex xs12 md4 style="position:relative">
												<div class="doughChart-title">Assets</div>
												<doughnut-chart :chart-data="assetsDataCollection"></doughnut-chart>
												<div class="doughChart-date">As of 20 February 2014</div>
											</v-flex>
											<v-flex xs12 md8>
												<div v-for="asset in Assets" class="asset-table" :style="asset.style">
													<v-layout row wrap class="hundredWidth">
														<v-flex xs3>
															<div style="font-weight:bold">{{ asset.name}}</div>
														</v-flex>
														<v-flex xs4>
															<div>{{ asset.numOfAccounts}} accounts</div>
														</v-flex>
														<v-flex xs1>
															<div>IDR</div>
														</v-flex>
														<v-flex xs4>
															<div>{{ asset.credit}}</div>
														</v-flex>
													</v-layout>
													<div v-for="branch in asset.branches" v-if="asset.branches.length > 0" class="asset-desc-table">
														<v-layout row wrap class="hundredWidth" >
															<v-flex xs3>
																<div class="adt-name">{{ branch.name }}</div>
															</v-flex>
															<v-flex xs4>
																<div class="adt-etc">{{ branch.numOfAccounts }} accounts</div>
															</v-flex>
														</v-layout>
													</div>
												</div>
												<div class="boldSeparator"></div>
												<v-layout row wrap class="hundredWidth ao-conclusion-container">
													<v-flex xs3>
														<div style="font-weight:bold">Assets</div>
													</v-flex>
													<v-flex xs4>
														<div >44 accounts</div>
													</v-flex>
													<v-flex xs1>
														<div style="font-weight:bold">IDR</div>
													</v-flex>
													<v-flex xs4>
														<div style="font-weight:bold">1,100,000,000.00</div>
													</v-flex>
												</v-layout>
											</v-flex>
										</v-layout>
										<div class="separator"></div>
										<v-layout row wrap class="hundredWidth">
											<v-flex xs12 md4 style="position:relative">
												<div class="doughChart-title">Liabilities</div>
												<doughnut-chart :chart-data="liabilitiesDataCollection"></doughnut-chart>
												<div class="doughChart-date">As of 20 February 2014</div>
											</v-flex>
											<v-flex xs12 md8>
												<div v-for="liabilities in Liabilities" :style="liabilities.style">
													<v-layout row wrap class="hundredWidth">
														<v-flex xs3>
															<div style="font-weight:bold">{{ liabilities.name}}</div>
														</v-flex>
														<v-flex xs4>
															<div>{{ liabilities.numOfAccounts}} accounts</div>
														</v-flex>
														<v-flex xs1>
															IDR
														</v-flex>
														<v-flex xs4>
															<div>{{ liabilities.credit}}</div>
														</v-flex>
													</v-layout>
												</div>
												<div class="boldSeparator"></div>
												<v-layout row wrap class="hundredWidth ao-conclusion-container">
													<v-flex xs3>
														<div style="font-weight:bold">Liabilities</div>
													</v-flex>
													<v-flex xs4>
														<div >7 accounts</div>
													</v-flex>
													<v-flex xs1>
														<div style="font-weight:bold">IDR</div>
													</v-flex>
													<v-flex xs4>
														<div style="font-weight:bold">450,000,000.00</div>
													</v-flex>
												</v-layout>
											</v-flex>
										</v-layout>
									</div>
									
									<div class="view-more"> View more </div>
								</div>
							</v-flex>
							<v-flex d-flex class="hundredWidth">
								<div class="content-cards">
									<div class="content-subheader">
										<div class="title">Most Visited</div>
										<div class="close">X</div>
										<div class="clearfix"></div>
									</div>
									<div class="most-visited-icon-container">
										<div class="mv-icon">
											<v-btn outline fab>
												<v-icon>person</v-icon>
											</v-btn>
										</div>
										<div class="mv-icon">
											<v-btn outline fab>
												<v-icon>event_note</v-icon>
											</v-btn>
										</div>
										<div class="mv-icon">
											<v-btn outline fab>
												<v-icon>content_paste</v-icon>
											</v-btn>
										</div>
										<div class="mv-icon">
											<v-btn outline fab>
												<v-icon>swap_horiz</v-icon>
											</v-btn>
										</div>
										<div class="clearfix"></div>
									</div>
									<div class="most-visited-text">
										<div class="mv-text">
											Profile
										</div>
										<div class="mv-text">
											Account Summary
										</div>
										<div class="mv-text">
											Statement
										</div>
										<div class="mv-text">
											In House Transfer
										</div>
										<div class="clearfix"></div>
									</div>
								</div>
							</v-flex>
							<v-flex d-flex class="hundredWidth">
								<div class="content-cards">
									<div class="content-subheader">
										<div class="title">Forex Rate</div>
										<div class="close">X</div>
										<div class="clearfix"></div>
									</div>
									<div class="fr-date">As of 20 February 2014</div>
									<v-layout row wrap class="hundredWidth">
										<v-flex d-flex xs12 sm7 md7>
											<v-data-table
											v-bind:headers="forexRateHeader"
											:items="forexRateItems"
											hide-actions
											class="data-table"
											>
												<template slot="headerCell" scope="props">
													<span v-tooltip:bottom="{ 'html': props.header.text }" class="data-table-header">
											          {{ props.header.text }}
											        </span>
												</template>
												<template slot="items" scope="props">
													<td>{{ props.item.currency }}</td>
													<td class="text-xs-left">{{ props.item.buy }}</td>
													<td class="text-xs-left">{{ props.item.sell }}</td>
												</template>
											</v-data-table>
										</v-flex>
										<v-flex xs12 sm5 md5 class="fr-function">
											<span class="text">View Complete Forex Rate</span>
											<span class="text">View Interest Rate</span>
											<span class="text">My Bank Product Info</span>
											<span class="text">ATM & Branch Lunch</span>
										</v-flex>
									</v-layout>
								</div>
							</v-flex>
						</v-layout>
					</v-flex>
					<v-flex d-flex xs12 sm6 md6 class="content-wrapper-right">
						<v-layout row wrap  class="hundredWidth">
							<v-flex d-flex class="hundredWidth">
								<div class="content-cards">
									<div class="content-subheader">
										<div class="title">Receivables</div>
										<div class="close">X</div>
										<div class="clearfix"></div>
									</div>
									<div class="table-desc">
										<div class="left">Number of Transaction (20)</div>
										<div class="right">Total Amount (IDR 200,000,000.00)</div>
										<div class="clearfix"></div>
									</div>
									<v-data-table
									v-bind:headers="ReceiveableHeader"
									:items="ReceiveableItems"
									hide-actions
									class="data-table"
									>
										<template slot="headerCell" scope="props">
											<span v-tooltip:bottom="{ 'html': props.header.text }" class="data-table-header">
									          {{ props.header.text }}
									        </span>
										</template>
										<template slot="items" scope="props">
											<td>{{ props.item.name }}</td>
											<td class="text-xs-left">{{ props.item.amount }}</td>
											<td class="text-xs-left">{{ props.item.due }}</td>
										</template>
									</v-data-table>
								<v-btn class="primary white--text add">Create Receivable
									<v-icon dark right>arrow_drop_down</v-icon>
								</v-btn>
								<div class="view-more"> View more </div>
							</div>
						</v-flex>
						<v-flex d-flex class="hundredWidth">
							<div class="content-cards">
								<div class="content-subheader">
									<div class="title">Payables</div>
									<div class="close">X</div>
									<div class="clearfix"></div>
								</div>
								<div class="table-desc">
									<div class="left">Number of Transaction (20)</div>
									<div class="right">Total Amount (IDR 200,000,000.00)</div>
									<div class="clearfix"></div>
								</div>
								<v-data-table
								v-bind:headers="PayablesHeader"
								:items="PayablesItems"
								hide-actions
								class="data-table"
								>
									<template slot="headerCell" scope="props">
										<span v-tooltip:bottom="{ 'html': props.header.text }" class="data-table-header">
								          {{ props.header.text }}
								        </span>
									</template>
									<template slot="items" scope="props">
										<td>{{ props.item.name }}</td>
										<td class="text-xs-left">{{ props.item.amount }}</td>
										<td class="text-xs-left">{{ props.item.beneficiary }}</td>
										<td class="text-xs-left">{{ props.item.due }}</td>
									</template>
								</v-data-table>
							<v-btn class="primary white--text add">Create Payable
								<v-icon dark right>arrow_drop_down</v-icon>
							</v-btn>
							<div class="view-more"> View more </div>
						</div>
					</v-flex>
					<v-flex d-flex class="hundredWidth">
						<div class="content-cards">
							<div class="content-subheader">
								<div class="title">Profit and Loss</div>
								<div class="close">X</div>
								<div class="clearfix"></div>
							</div>
							<bar-chart :chart-data="profitLossDataCollection" style="margin: 15px 0 0;"></bar-chart>
							<v-data-table
								v-bind:headers="profitLossHeader"
								:items="profitLossItems"
								hide-actions
								class="data-table"
								>
								<template slot="items" scope="props">
									<td>{{ props.item.type }}</td>
									<td class="text-xs-left">{{ props.item.sep13 }}</td>
									<td class="text-xs-left">{{ props.item.oct13 }}</td>
									<td class="text-xs-left">{{ props.item.nov13 }}</td>
									<td class="text-xs-left">{{ props.item.dec13 }}</td>
									<td class="text-xs-left">{{ props.item.jan14 }}</td>
									<td class="text-xs-left">{{ props.item.feb14 }}</td>
								</template>
							</v-data-table>
							<v-btn class="primary white--text add">Financial Report
								<v-icon dark right>arrow_drop_down</v-icon>
							</v-btn>
							<div class="view-more"> View Detail </div>
						</div>
					</v-flex>
				</v-layout>
			</v-flex>
		</v-layout>
	</v-container>
	<!-- <div class="clearfix hidden-xs-only"></div> -->
</div>
</v-app>
</template>

<script>
const moment = require('moment');
import DoughnutChart from '@/components/DoughnutChart.vue'
import BarChart from '@/components/BarChart.vue'
export default {
	name: 'Content',
	components : {
		doughnutChart : DoughnutChart,
		barChart : BarChart
	},
	data () {
		return {
			date: moment(new Date()).format('dddd MMM DD YYYY, hh:mm:ss'),
			ReceiveableHeader: [
				{ text: 'Description',align: 'left',sortable: true,value: 'name'},
				{ text: 'Amount', value: 'amount', align: 'left',sortable: false},
				{ text: 'Due', value: 'due', align: 'left',sortable: false },
			],
			ReceiveableItems: [
				{
					value: true,
					name: 'INV101 - PT.ABC',
					amount: 'IDR '+ this.numberWithCommas(50000),
					due: moment(new Date('21-Jan-2014')).format('D-MMM-YYYY'),
				},
				{
					value: true,
					name: 'INV059 - Corporate ltd',
					amount: 'USD '+ this.numberWithCommas(1000),
					due: moment(new Date('1-Mar-2014')).format('D-MMM-YYYY'),
				},
				{
					value: true,
					name: 'INV099 - PT. Company Indonesia',
					amount: 'IDR '+ this.numberWithCommas(89000000),
					due: moment(new Date('1-Mar-2014')).format('D-MMM-YYYY'),
				}
				,
				{
					value: true,
					name: 'CHQ2014 - Incoming Cheque',
					amount: 'IDR '+ this.numberWithCommas(10000000),
					due: moment(new Date('5-Apr-2014')).format('D-MMM-YYYY'),
				}
				,
				{
					value: true,
					name: '2014022300189 - AutoDebit',
					amount: 'IDR '+ this.numberWithCommas(8700000),
					due: moment(new Date('5-Apr-2014')).format('D-MMM-YYYY'),
				}
			],
			PayablesHeader: [
				{ text: 'Description',align: 'left',sortable: true,value: 'name'},
				{ text: 'Amount', value: 'amount', align: 'left',sortable: false},
				{ text: 'Beneficiary', value: 'beneficiary', align: 'left',sortable: false},
				{ text: 'Due', value: 'due', align: 'left',sortable: false},
			],
			PayablesItems: [
				{
					value: true,
					name: 'INV101 - eInvoice',
					amount: 'IDR '+ this.numberWithCommas(30000000),
					beneficiary: 'PT. ABC',
					due: moment(new Date('2014-03-01')).format('D-MMM-YYYY'),
				},
				{
					value: true,
					name: '201401239089 - Single Transfer',
					amount: 'USD '+ this.numberWithCommas(800),
					beneficiary: 'John Lenon',
					due: moment(new Date('1-Dec-2014')).format('D-MMM-YYYY'),
				},
				{
					value: true,
					name: '201401231189 - Bill Payment',
					amount: 'IDR '+ this.numberWithCommas(2000000),
					beneficiary: 'Telkomsel',
					due: moment(new Date('30-Mar-2014')).format('D-MMM-YYYY'),
				},
				{
					value: true,
					name: 'CHQ2014 - Incoming Cheque',
					amount: 'IDR '+ this.numberWithCommas(10000000),
					beneficiary: 'PT. XYZ',
					due: moment(new Date('5-Apr-2014')).format('D-MMM-YYYY'),
				},
				{
					value: true,
					name: '2014022300189 - Tax Payment',
					amount: 'IDR '+ this.numberWithCommas(8700000),
					beneficiary: 'DJP',
					due: moment(new Date('5-Apr-2014')).format('D-MMM-YYYY'),
				}
			],
			Assets:[
				{name: 'My Bank', numOfAccounts: 40, credit: this.numberWithCommas(800000000),
					branches: [ 
						{name: 'Current', numOfAccounts: 40},
						{name: 'Saving', numOfAccounts: 5},
						{name: 'Time Deposit', numOfAccounts: 2},
					],
					style : {
						color: '#5b9bd5'
					}
				},
				{name: 'External Bank', numOfAccounts: 4, credit: this.numberWithCommas(300000000), branches:[],
					style : {
						color: '#ed7d31'
					}
				}
			],
			Liabilities:[
				{name: 'Loan', numOfAccounts: 2, credit: this.numberWithCommas(400000000),
					style : {
						color: '#4472c4'
					}
				},
				{name: 'Credit Card', numOfAccounts: 5, credit: this.numberWithCommas(50000000),
					style : {
						color: '#70ad47'
					}},
			],
			assetsDataCollection:{
	          //Data to be represented on x-axis
	          labels: ['My Bank','External Bank'],
	          datasets: [
	            {
	           	  label: '',
	              backgroundColor: ['#5b9bd5','#ed7d31'],
	              pointBackgroundColor: 'white',
	              borderWidth: 1,
	              pointBorderColor: '#249EBF',
	              //Data to be represented on y-axis
	              data: [800000,300000]
	            }
	          ]
	        },
	        liabilitiesDataCollection:{
	          //Data to be represented on x-axis
	          labels: ['Loan','Credit Card'],
	          datasets: [
	            {
	           	  label: '',
	              backgroundColor: ['#4472c4','#70ad47'],
	              pointBackgroundColor: 'white',
	              borderWidth: 1,
	              pointBorderColor: '#249EBF',
	              //Data to be represented on y-axis
	              data: [400000000,50000000]
	            }
	          ]
	        },
			profitLossDataCollection:{
			  //Data to be represented on x-axis
	          labels: ['Sep-13','Oct-13','Nov-13','Dec-13','Jan-14','Feb-14'],
	          datasets: [
	            {
	           	  label: 'Cash In',
	              backgroundColor: ['#5b9bd5','#5b9bd5','#5b9bd5','#5b9bd5','#5b9bd5','#5b9bd5'],
	              borderColor:['#5b9bd5','#5b9bd5','#5b9bd5','#5b9bd5','#5b9bd5','#5b9bd5'],
	              borderWidth: 2,
	              //Data to be represented on y-axis
	              data: [430000,500000,69000,290000,900000,530000]
	            },
	            {
	           	  label: 'Cash Out',
	              backgroundColor: ['#ed7d31','#ed7d31','#ed7d31','#ed7d31','#ed7d31','#ed7d31',],
	              borderColor:['#ed7d31','#ed7d31','#ed7d31','#ed7d31','#ed7d31','#ed7d31',],
	              borderWidth: 2,
	              //Data to be represented on y-axis
	              data: [320000,380000,100000,150000,400000,230000]
	            },
	          ]
          	},
	        forexRateHeader: [
				{ text: 'Currency',value: 'currency',align: 'left',sortable: true},
				{ text: 'Buy', value: 'buy', align: 'left' },
				{ text: 'Sell', value: 'sell', align: 'left' },
			],
	        forexRateItems:[
	        	{value: true, currency: 'USD', buy: this.currencyFormat(11520), sell: this.currencyFormat(11490)},
	        	{value: true, currency: 'SGD', buy: this.currencyFormat(9213.65), sell: this.currencyFormat(9179.65)},
	        	{value: true, currency: 'EUR', buy: this.currencyFormat(15773.89), sell: this.currencyFormat(15673.89)},
	        	{value: true, currency: 'AUD', buy: this.currencyFormat(10691.33), sell: this.currencyFormat(10611.33)},
	        	{value: true, currency: 'JPY', buy: this.currencyFormat(114.67), sell: this.currencyFormat(111.67)}
	        ],
	        profitLossHeader:[
	        	{ text: 'Type', value: 'type',align: 'left',sortable: false},
	        	{ text: 'Sep-13', value: 'sep13',align: 'left',sortable: false},
				{ text: 'Oct-13', value: 'oct13', align: 'left',sortable: false},
				{ text: 'Nov-13', value: 'nov13', align: 'left',sortable: false},
				{ text: 'Dec-13', value: 'dec13', align: 'left',sortable: false},
				{ text: 'Jan-14', value: 'jan14', align: 'left',sortable: false},
				{ text: 'Feb-14', value: 'feb14', align: 'left',sortable: false}
	        ],
	        profitLossItems:[
	        	{value: true, type:'Cash In',sep13:this.numberWithCommas(430000),oct13:this.numberWithCommas(500000),nov13:this.numberWithCommas(69000),dec13:this.numberWithCommas(290000),jan14:this.numberWithCommas(900000),feb14:this.numberWithCommas(530000)},
	        	{value: true, type:'Cash Out',sep13:this.numberWithCommas(320000),oct13:this.numberWithCommas(380000),nov13:this.numberWithCommas(100000),dec13:this.numberWithCommas(150000),jan14:this.numberWithCommas(400000),feb14:this.numberWithCommas(230000)},
	        ]
		};
	},
	methods : {
		numberWithCommas(x) {
		    var parts = x.toString().split(".");
		    parts[0] = parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ",");
		    return parts.join(".");
		},
		currencyFormat(n){
			return Number(n.toFixed(2)).toLocaleString();
		}
	}
};
</script>

<style lang="css" scoped>
.appDivEdited{
	/*min-height: 80vh;*/
	height: auto;
	/*max-height: 100vh;*/
	padding: 2% 0;
	background: #ffffff;
}
.header{
	width: 100%;
	display: inline-block;
	padding: 0 5% 0;
	text-align: center;
}
.page-title{
	font-size: 2rem;
	color :#000000;
}
.user-last-login{
	margin: 2.5% 0;
}
.user-last-login .text{
	display: inline-block;
	vertical-align: middle;
	color: #c8c9d1;
}
.user-customised .text .icon{
	color: #81b3e3;
}
.user-customised .text{
	display: inline-block;
	vertical-align: middle;
	color: #81b3e3;
	cursor: pointer;
}
.content-wrapper{
	margin: 2% 4% 0;
	border: 3px solid #e2e2e2;
	border-radius: 1px;
	padding: 2% 1%;
}
.content-cards{
	position: relative;
	width: 100%;
	height: auto;
	border: 1px solid #f8f8f8;
	margin: 5% 0;
	padding: 10px;
	-moz-box-shadow:    2px 2px 5px 1px #ccc;
	-webkit-box-shadow: 2px 2px 5px 1px #ccc;
	box-shadow:         2px 2px 5px 1px #ccc;
}
.content-cards .data-table{
	margin: 10px;
}
.data-table .data-table-header{
	color: #0d7fca!important;
	font-weight: bold!important;
	font-size: 1.1rem;
}
.content-cards .view-more{
	position: absolute;
	bottom: 5px;
	right: 10px;
	color:#5151ff;
	font-size: 0.8rem;
	cursor: pointer;
}
.content-cards .content-subheader{
	position: relative;
	background: #f2f2f2;
	padding: 10px;
}
.content-cards .content-subheader .title{
	float: left;
}
.content-cards .content-subheader .close{
	float: right;
	color: #888786;
	font-size: 20px !important;
	font-weight: 500;
	line-height: 1 !important;
	letter-spacing: 0.02em !important;
	cursor: pointer
}
.content-cards .add{
	text-transform: none;
	margin: 0;
}
.user_logo{
	width: 90%;
	display: inline-block;
	vertical-align: middle;
}
.general-content{
	line-height: 25px;
}
.general-content.name{

}
.general-content.user{

}
.general-content.date{
	font-size: 0.85rem;
}
.general-content.messages{
	font-size: 0.85rem;
}
.general-content.task{
	font-size: 0.85rem;
}
.table-desc{
	position: relative;
	margin: 5px;
}
.table-desc .left{
	text-align: center;
	float: none!important;
	margin: 2px 0;
}
.table-desc .right{
	text-align: center;
	float: none!important;
	margin: 2px 0;
}
.most-visited-icon-container{
	width: 95%;
	margin: 2.5% 0;
}
.most-visited-icon-container .mv-icon{
	float: left;
	width: 25%;
	text-align: center;
}
.most-visited-text{
	width: 95%;
	margin: 2.5% 0;
}
.most-visited-text .mv-text{
	float: left;
	width: 25%;
	text-align: center;
}
.doughChart-title, .doughChart-date{
    text-align: center;
    /* vertical-align: middle; */
    width: 100%;
    font-size: 0.9rem;
}
.doughChart-date{
	margin: 7px 0;
	font-style: italic;
}
.fr-date{
	margin: 15px 10px 0;
}
.fr-function{

}
.fr-function .text{
	color:#674cff;
	text-align: center;
	line-height: 35px;
	cursor: pointer;
}
.asset-desc-table{

}
.asset-desc-table .adt-name{
	margin: 0 0 0 10px;
	font-size: 0.95rem;
}
.asset-desc-table .adt-etc{
	color: #bdbdbd;
	font-size: 0.95rem;
}
.ao-conclusion-container{
	overflow: auto;
	scroll-behavior: smooth;
}
@media only screen and (min-width: 600px) and (max-width: 960px){
	.header{
		display: flex;
		padding: 0 3% 0;
		text-align: left;
	}
	.user-last-login{
		margin: 0 2.5%;
	}
	.content-wrapper{
		margin: 2% 2% 0;
	}
	.content-cards{
		width: 47%;
		margin: 1.5%;
		/*float:left;*/
		height: auto;
	}
	.doughChart-title, .doughChart-date{
	    text-align: center;
	    /* vertical-align: middle; */
	    width: 100%;
	    font-size:0.85rem;
	}
	.fr-function{
		padding: 15% 15px!important;
	}
	.fr-function .text{
		text-align: left;
		line-height: 45px;
	}
	.content-cards .view-more{
		font-size: 1rem;
	}
}
@media only screen and (min-width: 960px){
	.header{
		display: flex;
		text-align: left;
		padding: 0 12% 0;
	}
	.user-last-login{
		margin: 0 2.5%;
	}
	.content-wrapper{
		margin: 2% 11% 0;
	}
	.content-cards{
		width: 47%;
		margin: 1.5%;
		/*float:left;*/
		height: auto;
	}
	.table-desc .left{
		float: left!important;
	}
	.table-desc .right{
		float: right!important;
	}
	.doughChart-title, .doughChart-date{
	    text-align: center;
	    /* vertical-align: middle; */
	    width: 100%;
	    font-size:0.85rem;
	}
	.fr-function{
		padding: 15% 15px!important;
	}
	.fr-function .text{
		text-align: left;
		line-height: 45px;
	}
	.content-cards .view-more{
		font-size: 1rem;
	}
}

</style>