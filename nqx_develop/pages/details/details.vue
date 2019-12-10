<template>
	<view>
		<view class="header">
			<image src="../../static/banner.png"></image>
			<view class="test">
				<text>抢购价:
				<h4 style="display: inline-block;">￥50</h4>
				<del style="color: #ccc;">90元</del></text>
			</view>
			<view class="integral">
				<text class="integral1">积分</text>
				<text class="integral2">积分抵20%</text>
			</view>
			<view class="text">
				<text style="margin-left:20upx">碧螺春云雾新绿茶罐装明前新茶<br></text>
				<text style="margin-left:20upx;
				font-size:30upx;
				display:block;
				">中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。</text>
			</view>
			<text class="detail">商品详情</text>
			<view class="detail-son">
				<view class="son1"
					v-for="(item,index) in list"
					:key='index'
				>
					<text>{{item}}</text>
				</view>
				<view class="son2"
					v-for="(itm,idx) in last"
					:key='idx'
				>
					<text>{{itm}}</text>
				</view>
			</view>
			<view class="unfold">
				<text>展开</text>
				<image src="../../static/shopping/details-2/middle_More.png" mode=""></image>
			</view>
		</view>
		<view class="content">
			<image src="../../static/shopping/details-1/1.jpg" mode="scaleToFill"></image>
			<text>大家还喜欢</text>
			<view class="shopping" v-for="(item, index) in shopList" :key="index">
				<view class="shop-div">
					<image src="../../static/shop_pic02.png"></image>
					<view class="shop-div1">
						<text class="title">{{ item.title }}</text>
						<text class="con">{{ item.conent }}</text>
						<text class="poi">￥{{ item.price }}</text>
						<text class="rx">热销推荐</text>
					</view>
				</view>
			</view>
			<image
			 class="qg"
			 @tap="show('QSPopup2')"
			 src="../../static/list_Button.png"></image>
			 <!-- @click="toAlert" -->
		</view>
		<QSPopup ref="QSPopup2" type="fadeInUp">
			<view class="footer">
				<view class="alert">
					<view class="a1">
						<image src="../../static/shopping/details-1/1.png" mode=""></image>
						<text class="t">碧螺春云雾新绿茶罐装明前新茶</text>
						<text class="p">￥50</text>
						<text class="k">库存456件</text>
					</view>
					<view class="a2">
						<text>类型</text>
						<view 
						v-for="(item,index) in alertList"
						:key="index"
						>
							<text class="type"
							@click="back(index)"
							:class="{active:index===steIndex}"
							>{{item}}</text>
						</view>
						<text class="num">数量</text>
						<image 
						class="btn"
						src="../../static/shopping/details-1/popup_Pickers.png"></image>
						<text class="count">{{count}}</text>
					</view>
					<image
					@click="toIndent"
					class="qg"
					src="../../static/list_Button.png"></image>
				</view>
			</view>
		</QSPopup>
	</view>
</template>

<script>
	//弹出层
	import QSPopup from '../../components/QS-popup/QS-popup.vue';
	export default {
		components:{QSPopup},
		data () {
			return {
				steIndex:0,
				isShow:false,
				count:1,
				list:[
					'品牌',
					'产品',
					'净含量',
					'包装方式'
				],
				last:[
					'碧螺春',
					'苏州',
					'259g',
					'罐装'
				],
				shopList: [
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
					},
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
					},
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
					},
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
					}
				],
				alertList:[
					'碧螺春',
					'红茶',
					'绿茶'
				]
			}
		},
		methods: {
			toIndent(){
				uni.navigateTo({
				    url: '../indent/indent'
				})
			},
			show(ref) {
				this.$refs[ref].show();
			},
			back(index){
				this.steIndex=index;
			}
		},
	}
</script>

<style lang="scss" scoped>
	.header{
		box-sizing: border-box;
		margin-bottom: 20upx;
		image{
			width: 100%;
			height: 500upx;
		}
		.test{
			color: #ff0000;
			margin:20upx;
			font-size: 40upx;
			h4{
				font-size: 50upx;
				margin-left: 20upx;
				margin-right: 50upx;
			}
		}
		.integral{
			margin:20upx;
			line-height: 140%;
			.integral1{
				color: #FFFFFF;
				display: inline-block;
				width: 120upx;
				height: 52upx;
				background:#FF3333;
				text-align: center;
				border-radius:50upx;
				font-size: 30upx;
			}
			.integral2{
				padding:5upx;
				margin-left: 50upx;
				text-align: center;
				border: 3px solid #FF3333;
				border-radius:50upx;
				font-size: 30upx;
			}
		}
		.text{
			width: 90%;
			margin-bottom: 40upx;
		}
		.detail{
			margin:20upx;
			border-left:6upx solid #FF3333;
			padding-left:20upx;
			font-weight: 600;
		}
		.detail-son{
			margin: 20upx;
			height: 200upx;
			font-size:30upx;
			overflow: hidden;
			.son1{
				color:rgba(120,120,120,1);
				margin-bottom:10upx;
			}
			.son2{
				margin-bottom:10upx;
				position: relative;
				left: 30%;
				bottom:100%;
				color:rgba(50,50,50,1);
			}
		}
		.unfold{
			font-size: 30upx;
			text-align: center;
			color:rgba(120,120,121,1);
			image{
				width: 40upx;
				height: 40upx;
				border: 1px dashed #CCCCCC;
				margin-left: 10upx;
				position: relative;
				top:10upx;
			}
		}
	}
	.content{
		width: 100%;
		image{
			width: 100%;
			height: 800upx;
			margin-bottom: 30upx;
		}
		text{
			margin:20upx;
			border-left:6upx solid #FF3333;
			padding-left:20upx;
			font-weight: 600;
		}
		.shop-div{
			width: 50%;
			margin-top: 20upx;
			background: #FFFFFF;
			box-sizing: border-box;
			float: left;
			image{
				width: 100%;
				height: 220upx;
				float: left;
			}
			.shop-div1{
				.title{
					margin-left:0upx;
					font-size: 22upx;
					border:none;
					color: #1E1E1E;
				}
				.con{
					font-size: 18upx;
					margin-top: 6upx;
					line-height:150%;
					border:none;
					margin-left:0upx;
					display: block;
					color: #8F8F94;
				}
				image{
					width: 30%;
					height: 50upx;
				}
				.poi{
					margin-top: 50upx;
					margin-bottom: 10upx;
					color: #FA436A;
					border:none;
					margin-left:0upx;
				}
				.rx{
					font-size: 20upx;
					color: #C0C0C0;
					border:none;
					margin-left:100upx;
				}
			}
		}
		.qg{
			margin-top: 30upx;
			width: 50%;
			height: 80upx;
			margin-left:25%;
		}
	}
	.footer{
		position: relative;
		.qg{
			margin-top: 15%;
			width: 50%;
			height: 80upx;
			margin-left:25%;
		}
		.alert{
			width: 100%;
			height: 600upx;
			position: absolute;
			bottom:120%;
			background: #FFFFFF;
			.a1{
				width: 100%;
				height: 40%;
				border-bottom: 1px solid #ececec;
				image{
					width: 240upx;
					height: 240upx;
					position: absolute;
					top:-10%;
					left:5%;
					border:3px solid #FFFFFF;
				}
				text{
					position: absolute;
					left:40%;
				}
				.t{
					top:5%;
					font-size:30upx;
					color:#1E1E1E;
				}
				.p{
					top:15%;
					color:#FF0060;
				}
				.k{
					font-size:26upx;
					top:30%;
					color:#323232;
				}
			}
			.a2{
				text{
					margin: 20upx;
					font-size: 30upx;
					color:#323232;
				}
				.type{
					float: left;
					text-align: center;
					width:20%;
					height: 40upx;
					background: #D2D2D2;
					border-radius: 30upx;
					display: inline-block;
				}
				.active{
					color:#FFFFFF;
					background:#FF0000;
					
				}
				.num{
					position: absolute;
					top:65%;
					left:0;
				}
				image{
					width: 30%;
					height: 70upx;
					position: absolute;
					top:65%;
					right:5%;
				}
				.count{
					position: absolute;
					top:64%;
				}
			}
		}
	}
</style>
