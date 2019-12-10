<template>
	<view class="content">
		<view class="head">
			<image src="../../static/shopping/indent/nav_Back.png" mode=""></image>
			<text>订单确认</text>
		</view>
		<view class="nav">
			<text style="left:5%;">星海</text>
			<text style="left:20%;">01234567891</text><br>
			<text style="top:45%">河南省郑州市</text>
			<image class="bon" src="../../static/image_arrow_mine.png"
			@click="toSite"></image>
		</view>
		<view class="details">
			<view class="det">
				<image src="../../static/shopping/details-1/1.png" mode=""></image>
				<text class="t">碧螺春云雾新绿茶罐装明前新茶</text>
				<text class="l">类型：碧螺春</text>
				<text class="p">￥50</text>
				<text class="j">积分抵20%</text>
				<text class="n">*{{count}}</text>
			</view>
			<view class="num">
				<text class="s">数量</text>
				<image class="le" src="../../static/shopping/indent/list_Middle_button_disabled.png"></image>
				<text class="l">{{count}}</text>
				<image class="ri" src="../../static/shopping/indent/list_Middle_button(1).png" mode=""></image>
			</view>
			<view class="num">
				<text class="s">配送</text>
				<text class="l" style="left:20%;width:40%;color:#323232;">普通快递&nbsp;免运费</text>
				<image class="ri" 
				style="border:1px dashed #C0C0C0;"
				src="../../static/shopping/indent/list_Top_Button.png" mode=""></image>
			</view>
			<view class="num">
				<text class="s">留言</text>
				<input type="text" placeholder="给商家留言 (限50字)">
			</view>
			<view class="num">
				<text class="s" 
				style="width:55%;">可用100积分抵扣￥10</text>
				<image class="ri"
				 style="width:15%;"
				 src="../../static/list_Bottom_button.png" mode=""></image>
			</view>
		</view>
		<view class="foot">
			<view class="left">
				<view class="top">
					<text class="a">实付款:</text>
					<text class="b">￥40元</text>
					<text class="c">免运费</text>
				</view>
				<text class="d">收货返10积分</text>
			</view>
			<button class="right" type="primary">立即支付</button>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				count:1
			}
		},
		methods:{
			toSite(){
				uni.navigateTo({
					url:'../site/site'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
	.content{
		width: 100%;
		height: 1600upx;
		background: #F5F5F5;
		position: relative;
		image{
			width: 60upx;
			height:60upx;
			border:1px dashed #000;
			margin: 30upx;
		}
		.head{
			width: 100%;
			height: 100upx;
			text{
				position: relative;
				top:-45%;
				font-weight: 800;
			}
		}
		.nav{
			margin: 20upx auto;
			width: 90%;
			height: 165upx;
			line-height: 200%;
			background: #FFFFFF;
			border:1upx dashed #000000;
			position: relative;
			text{
				display: inline-block;
				width: 35%;
				height: 33%;
				position: absolute;
				top:5%;
				left:5%;
				font-size: 32upx;
			}
			image{
				position: absolute;
				bottom:10%;
				right:0;
			}
		}
		.details{
			width: 90%;
			height:40%;
			background: #FFFFFF;
			margin-left: 5%;
			border-radius: 10upx;
			.det{
				padding-bottom: 2%;
				border-bottom:1px dashed #C0C0C0;
				image{
					width: 200upx;
					height: 200upx;
					float: left;
					border-radius: 30upx;
				}
				text{
					width: 60%;
					font-size: 26upx;
					display: inline-block;
				}
				.t{
					margin-top: 5%;
				}
				.l{
					margin-top: 2%;
				}
				.p{
					font-size:40upx;
					color: #FF3333;
					margin-top: 3%;
				}
				.j{
					color: #FF3333;
					margin-top:-1%;
				}
				.n{
					width: 10%;
					float: right;
					margin-top: -5%;
				}
			}
			.num{
				width: 100%;
				height:80upx;
				padding-bottom: 2%;
				border-bottom:1px dashed #C0C0C0;
				position: relative;
				text{
					display: inline-block;
					width: 20%;
					height: 100%;
					text-align: center;
					line-height: 300%;
					font-size:30upx;
				}
				.s{
					margin-right:100%;
				}
				.l{
					position: absolute;
					bottom:0;
					right:5%;
				}
				image{
					width: 40upx;
					height: 40upx;
					border:none;
				}
				.le{
					position: absolute;
					bottom:0;
					right:15%;
				}
				.ri{
					position: absolute;
					bottom:0;
					right:0%;
				}
				input{
					width:80%;
					height:100%;
					position: absolute;
					bottom:0;
					left:20%;
					font-size:30upx;
					color:#D2D2D2;
				}
			}
		}
		.foot{
			width:100%;
			height:7%;
			background: #FFFFFF;
			position:absolute;
			bottom:0;
			.left{
				width:60%;
				height:100%;
				text-align: center;
				float: left;
				.top{
					margin-top: 5upx;
					.a{
						font-size: 36upx;
						margin-right:15upx;
					}
					.b{
						font-size:42upx;
						color:#FF3333;
						margin-right:20upx;
					}
					.c{
						font-size: 30upx;
						color:#FF3333;
					}
				}
				.d{
					font-size:30upx;
					color:#FF3333;
					margin-right:42%;
				}
			}
			.right{
				width:40%;
				height:100%;
				float: right;
				background: #ff0000;
				line-height:300%;
			}
		}
	}
</style>
