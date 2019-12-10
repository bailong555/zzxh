<template>
	<view>
		<view v-for="item in definiteList" :key="item.id">
			<view class="definite">
				<view class="definite-fl">
					<h5>会议主题:{{ item.title }}</h5>
					<p>{{ item.status }}</p>
				</view>
				<text>{{ item.number }}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data () {
			return {
				definiteList: [
					{
						title: '书写荣光恰是风华正茂',
						status: '活动准时参加',
						number: '+6'
					},
					{
						title: '书写荣光恰是风华正茂',
						status: '活动迟到',
						number: '-3'
					},
					{
						title: '书写荣光恰是风华正茂',
						status: '活动缺席',
						number: '-5'
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
	.definite {
		height: 150rpx;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0 22rpx;
		border-bottom: 1px solid #ccc;
	}
	.definite-fl {
		width: 80%;
		font-size: 16px;
	}
	.definite-fl p {
		font-size: 12px;
		margin-top: 5px;
	}
	.definite text {
		font-size: 12px;
	}
</style>
