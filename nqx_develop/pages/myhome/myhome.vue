<template>
	<view>
		<view class="myhome">
			<image src="../../static/nav bar_bgd_mine.png"/>
			<view class="myhome-div">
				<view class="myhome-div1">
					<image src="../../static/mine_icon_head portrait.png"/>
					<p>超级管理员<text>VIP</text></p>
				</view>
				<view class="myhome-div2"> 
					<image src="../../static/mine_icon_edit.png"/>
				</view>
			</view>
		</view>
		<view class="myhome-main">
			<view class="myhome-main-div">
				<text>入会进度</text>
				<text style="float: right;margin-right: 15px;">未审核通过</text>
			</view>
			<view v-for="item in mainList" :key="item.id">
				<view class="myhome-main-div" @click="puer(item.id)">
					<text>{{ item.status }}</text>
				</view>
			</view>
			<view class="myhome-main-pueer">
				<view  v-for="item in pueerList" :key="item.id">
					<view  class="myhome-pueer-div" @click="navck(item.id)">
						<text>{{ item.status }}</text>
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
				mainList: [
					{ status: '会员缴纳', id:1},
					{ status: '缴费记录', id:2}
				],
				pueerList: [
					{ status: '我的报名', id:1},
					{ status: '我的积分', id:2},
					{ status: '我的发布', id:3},
					{ status: '我的发布二维码',  id:4},
				]
			}
		},
		methods: {
			puer(id) {
				if (id == 1) {
					uni.navigateTo({
						url: '/pages/myhome/dues'
					})
				} 
			},
			navck(id) {
				if (id == 2) {
					uni.navigateTo({
						url: '/pages/integral/integral'
					})
				} 
			}
		}
	}
</script>

<style lang="scss">
	.myhome {
		width: 100%;
		height: 500rpx;
		position: relative;
		image {
			width: 100%;
			height: 150px;
		}
	}
	.myhome-div {
		width: 85%;
		height: 300rpx;
		display: flex;
		justify-content: space-between;
		position: absolute;
		top: 30%;
	}
	.myhome-div1 {
		width: 50%;
		height: 100%;
		image {
			width: 80%;
			height: 80%;
		}
		p {
			width: 70%;
			padding-left: 25rpx;
			margin: 0;
			pagging: 0;
			font-size: $font-sm + 5upx;
			text {
				display: block;
				width: 30px;
				height: 15px;
				background: red;
				text-align: center;
				line-height: 15px;
				border-radius: 15rpx;
				color: #fff;
				font-size: 10px;
				float: right;
				margin-top: 3px;
			}
		}
	}
	.myhome-div2 {
		width: 50%;
		height: 100%;
		text-align: right;
		line-height: 550rpx;
		image {
			width: 50%;
			height: 50%;
		}
	}
	.myhome-main {
		padding: 0 22rpx;
	}
	.myhome-main-pueer {
		border-top: 1px solid #ccc;
		padding-top: 22rpx;
		margin-top: 22rpxn;
	}
	.myhome-main-div {
		width: 100%;
		height: 80rpx;
		line-height: 80rpx;
		background: url(../../static/image_arrow_home.png) no-repeat right;
		background-size: 8px;
		text {
			font-size: $font-sm + 5upx;
			float: left;
		}
		image {
			width: 20rpx;
			height: 20rpx;
			float: right;
			margin-top: 20rpx;
		}
	}
	.myhome-pueer-div {
		width: 100%;
		height: 80rpx;
		line-height: 80rpx;
		background: url(../../static/image_arrow_home.png) no-repeat right;
		background-size: 8px;
		text {
			font-size: $font-sm + 5upx;
			float: left;
		}
		image {
			width: 20rpx;
			height: 20rpx;
			float: right;
			margin-top: 20rpx;
		}
	}
</style>
