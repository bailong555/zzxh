<template>
	<view>
		<view class="taken" v-for="item in takenList" :key="item.id">
			<image :src=" item.url "/>
			<view class="taken-div">
				<view>
					<p>{{ item.title }}</p>
					<p>{{ item.time }}</p>
				</view>
				<text>{{ item.price }}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				takenList: [
					{
						url: '../../../static/banner.png',
						title: '微信充值',
						time: '2019-09-09',
						price: '500'
					},
					{
						url: '../../../static/banner.png',
						title: '微信充值',
						time: '2019-09-09',
						price: '500'
					},
					{
						url: '../../../static/banner.png',
						title: '微信充值',
						time: '2019-09-09',
						price: '500'
					},
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss" scoped>
	.taken {
		padding: 22rpx;
		width: 95%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		border-bottom: 1px solid #ccc;
	}
	.taken image {
		width: 100rpx;
		height: 100rpx;
	}
	.taken-div {
		width: 80%;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.taken-div p {
		font-size: $font-sm;
		margin-top: 5px;
	}
	.taken-div text {
		font-size: $font-sm + 5upx;
		color: #bbb;
	}
	.taken-div p:nth-of-type(1) {
		font-size: $font-lg;
	}
	.taken-div p:nth-of-type(2) {
		color: #bbb;
	}
</style>
