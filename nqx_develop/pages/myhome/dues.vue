<template>
	<view class="dues-page">
		<view class="dues-header">
			<view class="dues" v-for="item in duesList" :key="item.id">
				<p>{{ item.title }}</p>
				<p>收费账户:<text>{{ item.price }}</text></p>
				<p>缴费年数:<text>{{ item.year }}</text></p>
				<p>起始时间:<text>{{ item.startTime }}</text></p>
				<p>到期时间:<text>{{ item.endTime }}</text></p>
				<p>￥{{ item.price2 }}</p>
			</view>
		</view>
		<button type="warn" class="btn">已是会员立即续费</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				duesList: [
					{
						title: '恭喜您的资料审核通过成为会员',
						price: '郑州市女企业家协会',
						year: '一年',
						startTime: '2019-09-09',
						endTime: '2020-09-09',
						price2: '1000'
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.dues-page {
		min-height: 800px;
		background: #bbb;
		padding: 26rpx;
	}
	.dues-header {
		height: 500rpx;
		background: #fff;
	}
	.dues-header p {
		font-size: $font-sm + 5upx;
		margin-top: 10px;
	}
	.dues-header p text {
		font-size: $font-sm + 2upx;
		color: #ccc;
		margin-left: 10px;
	}
	.dues-header p:nth-of-type(6) {
		width: 100%;
		height: 150rpx;
		line-height: 150rpx;
		color: #FF0060;
		text-align: center;
		font-size: $font-lg + 15upx;
	}
	.btn {
		margin-top: 50px;
		font-size: $font-lg;
		background: #FF0060;
		border-radius: 10px;
	}
</style>
