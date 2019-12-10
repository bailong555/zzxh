<template>
	<view>
		<view class="integral-header">
			<p><text>{{ status }}</text>积分</p>
			<p><text @click="per">积分明细</text></p>
		</view>
	</view>
</template>

<script>
	export default {
		data () {
			return {
				status: '1000.0'
			}
		},
		methods: {
			per() {
				uni.navigateTo({
					url: '/pages/integral/integral-definite'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.integral-header {
		height: 200rpx;
		background: #FF106A;
		padding-top: 15px;
		border-top: 2px solid #fff;
	}
	.integral-header p {
		color: #fff;
		text-align: center;
		font-size: 12px;
	}
	.integral-header p:nth-of-type(1) text {
		font-size: 18px;
		padding-right: 15px;
	}
	.integral-header p:nth-of-type(2) text {
		display: block;
		width: 150rpx;
		height: 50rpx;
		line-height: 50rpx;
		border: 1px solid #fff;
		margin: 0 auto;
		border-radius: 5px;
		margin-top: 15px;
	}
</style>
