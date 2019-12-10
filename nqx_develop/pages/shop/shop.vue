<template>
	<view style="height: 100%;background: #F1F1F1;">
		<view class="shop">
			<text style="margin-left: 20upx;font-size: 30upx;">热搜:</text>
			<view 
			class="list"
			v-for="item in list" 
			:key="item.id">
				<text class="shop-spn">{{ item }}</text>
			</view><br>
			<view class="test"
			v-for="(itm,idx) in slist"
			:key='idx'
			:class="{active:idx===steIndex}"
			@click="back(idx)"
			>
				{{ itm }}
			</view>
		</view>
		<view class="main">
			<!-- 轮播图 -->
			<view class="sper">
			    <swiper class="swiper" 
					indicator-dots="true" 
					autoplay="true" 
					interval="2000" 
					duration="500">
			        <swiper-item class="prr">
			            <image src="../../static/hdxq_banner.png"/>
			        </swiper-item>
			        <swiper-item class="prr">
			            <image src="../../static/hdxq_banner.png"/>
			        </swiper-item>
			        <swiper-item class="prr">
			            <image src="../../static/hdxq_banner.png"/>
			        </swiper-item>
			    </swiper>
			 </view>
			 <view class="shopping" v-for="(item, index) in shopList" :key="index">
				<view class="shop-div">
					<image src="../../static/shop_pic02.png"></image>
					<view class="shop-div1">
						<text class="h5" style="margin-top:10upx;">{{ item.title }}</text>
						<text class="p">{{ item.conent }}</text><br>
						<text class="h6">抢购价:<text>￥{{ item.price }}</text>
							<text class="del">90元</text>
						</text>
						<image :src=" item.url "
							@click="toDetails"
						/>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data () {
			return {
				steIndex:0,
				list: [
					'茶叶',
					'速食',
					'饮品',
					'饮品'
				],
				slist: [
					'饮品',
					'饮品',
					'日用品',
					'保健品',
					'书籍'
				],
				//商品列表
				shopList: [
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						url: '../../static/list_Button.png'
					},
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						url: '../../static/list_Button.png'
					},
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						url: '../../static/list_Button.png'
					},
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						url: '../../static/list_Button.png'
					}
				]
			}
		},
		onLoad: {
		},
		methods: {
			toDetails(){
				uni.navigateTo({
				    url: '../details/details'
				});
			},
			back(index){
				this.steIndex=index;
			}
		}
	}
</script>

<style lang="scss" scoped>
	.shop{
		width: 100%;
		height: 400upx;
		background-image: url(../../static/nav_bar_bgd.png);
		white-space:nowrap;
		.test{
			display:inline-block;
			font-size: 32upx;
			color: #FFFFFF;
			margin-top: 30upx;
			margin-left: 36upx;
			text-align: center;
			width: 120upx;
			height: 50upx;
			display: inline-block;
		}
		.active{
			border-radius: 30upx;
			background:#ccc;
		}
		.list{
			margin-top:20upx;
			width:100upx;
			display: inline-block;
			border: 1px solid #FFFFFF;
			border-radius: 50upx;
			text-align: center;
			margin-left: 20upx;
			font-size:30upx;
			box-sizing: border-box;
			color: #FFFFFF;
		}
	}
	.main{
		width: 96%;
		margin:-200upx auto;
		.swiper{
			.prr{
				image{
					width: 100%;
					height: 100%;
				}
			}
		}
		.shop-div{
			width: 100%;
			height: 300upx;
			margin-top: 20upx;
			border-radius: 20upx;
			background: #FFFFFF;
			box-sizing: border-box;
			image{
				width: 38%;
				height: 300upx;
				float: left;
				margin-right: 2px;
			}
			.shop-div1{
				.h5{
					line-height: 200%;
					font-size: 30upx;
					display: inline-block;
				}
				.p{
					font-size: 24upx;
					margin-top: 6upx;
				}
				image{
					width: 30%;
					height: 50upx;
				}
				.h6{
					margin-top: 50upx;
					margin-bottom: 10upx;
					color: #FA436A;
					font-size:40upx;
					line-height: 200%;
					text{
						font-size: 36upx;
					}
					.del{
						margin-left: 100upx;
						color: #C0C0C0;
						font-size:30upx;
						text-decoration:line-through;
					}
				}
			}
		}
	}
</style>
