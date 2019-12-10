<template>
	<view>
		<!-- 头部轮播 -->
	    <view class="uni-padding-wrap">
	        <view class="page-section swiper">
	            <view class="page-section-spacing">
	               <swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
	                    <swiper-item class="prr">
	                        <view class="swiper-item uni-bg-red"><img src="../../static/hdxq_banner.png"/></view>
	                    </swiper-item>
	                    <swiper-item>
	                        <view class="swiper-item uni-bg-green">B</view>
	                    </swiper-item>
	                    <swiper-item>
	                        <view class="swiper-item uni-bg-blue">C</view>
	                    </swiper-item>
	                 </swiper>
	            </view>
	        </view>
	    </view>
		<!-- 分类 -->
		<view class="cate-section">
			<view class="purl" v-for="item in list" :key="item.id">
				<view class="cate-item" @click="openinfo(item.id)">
					<image :src=" item.url "></image>
					<text>{{ item.status }}</text>
				</view>
			</view>
		</view>
		<!-- 活动 -->
		<view class="activity">
			<view class="activity-sent">
				<view>{{ status.poper }}</view>
				<navigator url="/pages/shaky/shaky" style="width: 50%;">
					<view style="text-align: right;">{{ status.more }}</view>
				</navigator>
			</view>
			<view class="activity-peer">
				<image src="../../static/banner.png"/>
			</view>
			<view class="activity-ent">
				<p>会议主题：<text>测试活动</text></p>
				<p>时间：<text>2019-11-8 14：30</text></p>
				<p>会议主题：<text>测试活动</text></p>
				<p>已报名：<text>2人</text></p>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
			data() {
			    return {
					//轮播图
			        background: ['color1', 'color2', 'color3'],
			        indicatorDots: true,
			        autoplay: true,
			        interval: 2000,
			        duration: 500,
					list: [
						{ status: '活动', url: '../../static/home_icon_activity.png', id:1},
						{ status: '申请入会', url: '../../static/home_icon_question.png', id:2},
						{ status: '调查问卷', url: '../../static/home_icon_shop.png', id:3},
						{ status: '商城', url: '../../static/home_icon_VIP.png', id:4},
					],
					//活动
					status: {
						poper: '最新活动',
						more: '更多>'
					}
			    }
		    },
		// },
 		onLoad() {

		},
		methods: {
			// 头部轮播
			changeIndicatorDots(e) {
			    this.indicatorDots = !this.indicatorDots
			},
			changeAutoplay(e) {
			    this.autoplay = !this.autoplay
			},
			intervalChange(e) {
			    this.interval = e.target.value
			},
			durationChange(e) {
			    this.duration = e.target.value
			},
			//页面跳转
			openinfo(id) {
				if (id == 1) {
					uni.navigateTo({url: '/pages/shaky/shaky'})
				} else if (id == 4) {
					uni.navigateTo({url: '/pages/shop/shop'})
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50upx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
	.prr {
		background: red;
		img {
			width: 100%;
			height: 100%;
		}
	}
	.cate-section {
		height: 200px;
		padding: 30rpx 22rpx; 
		.purl {
		 	display: block;
		 	width: 50%;
		 	height: 50%;
		 	float: left;
		 }
		.cate-item {
			float: left;
			width: 100%;
			height: 100%;
			position: relative;
			image {
				width: 100%;
				height: 100%;
			}
			text {
				position: absolute;
				top: 15%;
				left: 10%;
				font-size: $font-sm + 5upx;
				color: #fff;
			}
		}
	}
	.activity {
		padding: 30rpx 30rpx;
		.activity-sent {
			display: flex;
			justify-content: space-between;
			height: 20px;
			line-height: 20px;
			border-left: 3px solid red;
			padding-left: 22rpx;
			view {
				// width: 50%;
				font-size: $font-sm + 5upx;
			}
		}
		.activity-peer {
			margin-top: 10px;
			width: 100%;
			height: 120px;
			image {
				width: 100%;
				height: 100%;
			}
		}
		.activity-ent {
			margin-top: 10px;
			border-bottom: 1px dashed #ccc;
			p {
				font-size: $font-sm + 5upx;
				color: #ccc;
				text {
					color: black;
				}
			}
		}
	}
</style>
