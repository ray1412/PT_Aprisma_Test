<template>
	<v-app class="appDivEdited">
		<v-navigation-drawer v-model="sideNav" temporary>
			<v-list>
				<v-list-tile>
					<v-list-tile-action>
						<v-icon x-large large>account_circle</v-icon>
					</v-list-tile-action>
					<v-list-tile-content>
						<div>Jeremy Brown</div>
						<div>PT. Aprisma - ID2357519</div>
					</v-list-tile-content>
				</v-list-tile>
				<v-list-tile v-for="item in menuItems" :key="item.title" :to="item.link">
					<v-list-tile-action>
						<v-icon>{{item.icon}}</v-icon>
					</v-list-tile-action>
					<v-list-tile-content>{{item.title}}</v-list-tile-content>
				</v-list-tile>
				<v-list-tile>
					<v-list-tile-action>
						<v-icon>exit_to_app</v-icon>
					</v-list-tile-action>
					<v-list-tile-content>Sign Out</v-list-tile-content>
				</v-list-tile>
			</v-list>
		</v-navigation-drawer>
		<v-toolbar class="info edited-toolbar" dark>
			<v-toolbar-side-icon @click.stop="sideNav = !sideNav" class="hidden-sm-and-up"></v-toolbar-side-icon>
			<v-toolbar-title id="aprisma_logo">
				<img src="../assets/img/aprisma_logo.png"/>
				<div class="vertical-align-middle"></div>
			</v-toolbar-title>
			<v-spacer></v-spacer>
			<v-toolbar-items class="hidden-xs-only">
				<v-btn flat>
					<div class="header-name">Jeremy Brown <br> <span class="header-id">PT. Aprisma - ID2357519</span></div>
					<v-icon right x-large large>account_circle</v-icon>
				</v-btn>
			</v-toolbar-items>
			<div class="hidden-xs-only">
				<v-btn icon flat v-for="item in menuItems" :key="item.title" :to="item.link">
					<v-icon>{{item.icon}}</v-icon>
				</v-btn>
			</div>
			<v-toolbar-items class="hidden-xs-only">
				<v-btn flat>
					<v-icon left>exit_to_app</v-icon>
					<span>Sign Out</span>
				</v-btn>
			</v-toolbar-items>
			</v-toolbar>
			<v-tabs v-model="active" :scrollable="true">
				<v-tabs-bar class="white edited-tabs-bar">
					<v-tabs-slider class="yellow"></v-tabs-slider>
						<v-tabs-item
						v-for="tab in normalTabs"
						:key="tab.text"
						:href="'#' + tab"
						ripple
						class="tabs-item"
						>
							<v-icon>{{tab.icon}}</v-icon><font :style="tab.style">{{ tab.text }}</font>
						</v-tabs-item>
				        <v-menu 
				        v-for="tab in leftTabsDropDown"
				        :key="tab.text"
						:href="'#' + tab"
						ripple
						class="tabs-item"
						>
					        <v-tabs-item slot="activator" :style="tab.style">
					          <font v-bind:style="tab.style">{{ tab.text }}</font>
					          <v-icon>arrow_drop_down</v-icon>
					        </v-tabs-item>
					        <v-list>
				          		<v-list-tile 
				          		v-for="n in 4" 
				          		v-bind:key="n" 
				          		@click=""
				          		>
					      			Item {{ n }}
				      			</v-list-tile>
					        </v-list>
				      	</v-menu>
				      	<v-spacer></v-spacer>
				      	<v-menu 
				        v-for="tab in rightTabsDropDown"
				        :key="tab.text"
						:href="'#' + tab"
						ripple
						class="tabs-item"
						>
					        <v-tabs-item slot="activator" v-bind:style="tab.style">
					          <font v-bind:style="tab.style">{{ tab.text }}</font>
					          <v-icon>arrow_drop_down</v-icon>
					        </v-tabs-item>
					        <v-list v-for="n in 4" v-bind:key="n">
					          <v-list-tile @click="">Item {{ n }}</v-list-tile>
					        </v-list>
				      	</v-menu>
				</v-tabs-bar>
			</v-tabs>
		<!-- <app-content></app-content> -->
	</v-app>
</template>

<script>
// import Content from '@/components/Content.vue'
export default {
	name: 'Main',
	// components:{
	// 	appContent: Content
	// },
	data () {
		return {
			sideNav: false,
			menuItems : [
				{icon: 'notifications_active', title: 'Notifications', link:''},
			],
			normalTabs: [
				{icon: 'home', text: '',style :{textTransform: 'none'}},
				{icon: '', text: 'My Tasks',style :{color:'#a4a9b4',textTransform: 'none'}},
			],
			leftTabsDropDown: [
				{text: 'Accounts',content: 'ccc',style :{color:'#a4a9b4',textTransform: 'none'}},
				{text: 'Transactions',content: 'ddd',style :{color:'#a4a9b4',textTransform: 'none'}},
				{text: 'Transfers',content: 'eee',style :{color:'#a4a9b4',textTransform: 'none'}},
				{text: 'Payments',content: 'fff',style :{color:'#a4a9b4',textTransform: 'none'}},
				{text: 'Liquidity',content: 'ggg',style :{color:'#6991be',textTransform: 'none'}},
			],
			rightTabsDropDown: [
				{text: 'Utilities',content: 'hhh',style :{color:'#a4a9b4',textTransform: 'none'}},
				{text: 'Help',content: 'iii',style :{color:'#a4a9b4',textTransform: 'none'}},
			],
			active: null,
		};
	},
	computed:{

	},
	methods:{

	}
};
</script>

<style lang="css" scoped>
.appDivEdited{
	min-height: 10vh;
	height: auto;
	border-bottom: 2px solid #f5f6f7;
}
#aprisma_logo{
	width: 100%;
	max-width: none;
	height: 100%;
}
#aprisma_logo img{
	cursor: pointer;
	/*width: 50%;*/
	display: inline-block;
	vertical-align: middle;
	margin: 0 25% 0 25%;
}
.header-name{
	text-align: right;
}
.header-id{
	color: #5087b7;
}
.tabs-item{
	color: #d9dadc;
}
.edited-tabs-bar{
	padding: 0;
}
.edited-toolbar{
	background: #2469a5 !important;	
	padding: 0;
}
@media only screen and (min-width: 600px) and (max-width: 960px){
	#aprisma_logo{
		width: 100%;
		max-width: 100%;
		height: 100%;

	}
	#aprisma_logo img{
		cursor: pointer;
		width: 45%;
		display: inline-block;
		vertical-align: middle;
		margin: 0 5% 0;
	}
	.edited-toolbar{
		padding: 0 0 0;
	}
	.edited-tabs-bar{
		padding: 0 0 0;
	}
} 
@media only screen and (min-width: 960px){
	#aprisma_logo{
		width: 100%;
		max-width: 100px;
		height: 100%;

	}
	#aprisma_logo img{
		cursor: pointer;
		width: 100%;
		margin: 0;
		display: inline-block;
		vertical-align: middle;
	}
	.edited-toolbar{
		padding: 0 10% 0;
	}
	.edited-tabs-bar{
		padding: 0 10% 0;
	}
}
</style>