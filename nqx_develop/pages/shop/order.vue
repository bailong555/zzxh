<template>
	<view class="content">
		<view class="order-header">
			<view class="order-header-div">
				<p>星海<text>1235678987</text></p>
				<p>河南省郑州市梧桐街22号</p>
			</view>
			<image src="../../static/list_Top_Button.png"/>
		</view>
		<view class="order-main">
			<view class="shop-div">
				<image src="../../static/shop_pic02.png"></image>
				<view class="shop-div1">
					<h5>碧螺春云雾新绿茶罐装明前新茶</h5>
					<p>类型:碧螺春</p>
					<p>￥50</p>
					<p>积分抵20%</p>
				</view>
			</view>
			<view class="shop-div2">
				<view>数量</view>
				<view>配送</view>
				<view>留言</view>
				<view>可用100积分抵扣￥10</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data () {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		min-height: 1200px;
		padding: 15px 22rpx;
		background: #F5F5F5;
	}
	.order-header {
	    width: 95%;
		height: 79px;
		padding: 0 22rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		background: url(../../static/list_Backgroud.png) no-repeat;
		image {
			width: 30px;
			height: 30px;
		}
	}
	.order-header-div {
		p {
			font-size: $font-sm + 10upx;
		}
		p:nth-of-type(1) {
			margin-bottom: 15rpx;
			text {
				padding-left: 50rpx;
			}
		}
	}
	.order-main {
		width: 100%;
		height: 300px;
		border-radius: 15px;
		background: #fff;
		margin-top: 15px;
	}
	.shop-div {
		width: 93%;
		height: 265rpx;
		background: #fff;
		padding: 10rpx 22rpx;
		border-radius: 15px;
		margin-top: 10px;
		display: flex;
		justify-content: space-between;
		image {
			width: 100px;
			height: 100px;
		}
	}
	.shop-div1 {
		margin-right: 15px;
		h5 {
			font-size: 14px;
			margin-top: 5px;
		}
		p {
			font-size: 10px;
			margin-top: 15rpx;
		}
		p:nth-of-type(1) {
			color: #323232;
		}
		p:nth-of-type(2) {
			color: #FF0060;
			font-size: 17px;
		}
		p:nth-of-type(3) {
			color: #FF0060;
		}
		image {
			width: 50%;
			height: 50rpx;
			margin-top: 22rpx;
		}
	}
	.shop-div2 {
		view {
			width: 94%;
			height: 30px;
			line-height: 30px;
			padding: 0 22rpx;
			color: #1E1E1E;
			font-size: $font-sm + 5upx;
			border-top: 1px solid #E6E6E6;
		}
	}
</style>
