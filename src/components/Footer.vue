<template>
	<v-app class="appDivEdited">
		<div class="footer-wrapper">
			<div class="footer-languange">
				<div class="text">Bahasa</div>
				<span>&nbsp;&nbsp;|&nbsp;&nbsp;</span>
				<div class="text">English</div>
			</div>
			<div class="footer-etc">
				<div class="text">Rates</div>
				<div class="text">Terms & Condition</div>
				<div class="text">Privacy Policy</div>
				<div class="text">Help</div>
				<div class="text">Contact Us</div>
			</div>
			<div class="clearfix" hidden-xs-only></div>
		</div>
		<div class="footer-separator"></div>
		<div class="footer-wrapper">
			<v-layout row wrap>
				<v-flex xs12 sm3 md3>
					<div class="footer-image"><img src="../assets/img/wirecard-logo.png"/></div>
				</v-flex>
				<v-flex xs12 sm8 md8 offset-sm1 offset-md1>
					<div class="footer-compDesc">MyBank internet Business is Services mark of Pt MyBank, TBK<br>Lorem ipsum dolor sit amet consectetur adipisicing elit sed do.</div>
				</v-flex>
			</v-layout>
		</div>
	</v-app>
</template>

<script>
export default {

  name: 'Footer',

  data () {
    return {

    };
  }
};
</script>

<style lang="css" scoped>
.appDivEdited{
	min-height: 10vh;
	height: auto;
	border-top: 2px solid #f5f6f7;
	background: #ffffff;
}
.footer-wrapper{
	padding: 0;
	margin: 10px 0;
}
.footer-separator{
	width: 100%;
	border: 1px solid #f5f6f7;
	margin: 0;
}
.footer-languange{
	width: 100%;
	float:none;
	text-align: center;
}
.footer-languange .text{
	cursor: pointer;
	display: inline-flex;
}
.footer-languange .text.active{

}
.footer-etc{
	float:none;
	display: block;
	text-align: center;
	margin: 15px 0;
}
.footer-etc .text{
	cursor: pointer;
	margin: 0 10px;
	line-height: 25px;
}
.footer-image{
	position: relative;
	text-align: center;
	margin: 0 0 10px;
}
.footer-image img{
	width: 50%;
}
.footer-compDesc{
	text-align: center;
	padding: 0 12.5%;
}
@media only screen and (min-width: 600px) and (max-width: 960px){
	.footer-wrapper{
		padding: 0 10% 0;
	}
	.footer-separator{
		width: 80%;
		margin: 0 10% 0;
	}
	.footer-languange{
		width: auto;
		display: inline-flex;
		float:left;
	}
	.footer-languange .text{
		cursor: pointer;
	}
	.footer-languange .text.active{

	}
	.footer-etc{
		float:right;
		display: inline-flex;
		margin: 0;
	}
	.footer-etc .text{
		cursor: pointer;
		margin: 0 10px;
	}
	.footer-image{
		margin: 0;
	}
	.footer-image img{
		width: 100%;
	}
	.footer-compDesc{
		text-align: left;
		padding: 0;
	}
}
@media only screen and (min-width: 960px){
	.footer-wrapper{
		padding: 0 10% 0;
	}
	.footer-separator{
		width: 80%;
		margin: 0 10% 0;
	}
	.footer-languange{
		width: auto;
		display: inline-flex;
		float:left;
	}
	.footer-languange .text{
		cursor: pointer;
	}
	.footer-languange .text.active{

	}
	.footer-etc{
		float:right;
		display: inline-flex;
		margin: 0;
	}
	.footer-etc .text{
		cursor: pointer;
		margin: 0 10px;
	}
	.footer-image{
		margin: 0;
	}
	.footer-image img{
		width: 100%;
	}
	.footer-compDesc{
		text-align: left;
		padding: 0;
	}
}
</style>