<template>
	<view class="enroll-page">
		<view class="enroll" v-for="item in list" :key="item.id">
			<image :src=" item.url "></image>
			<view class="enroll-ent">
				<p>会议主题：<text>{{ item.title }}</text></p>
				<p>时间：<text>{{ item.time }}</text></p>
				<p>地址：<text>{{ item.address }}</text></p>
				<p>已报名：<text>{{ item.people }}人</text></p>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data () {
			return {
				//活动列表
				list: [
					{
						url: '../../static/banner.png',
						title: '测试活动',
						time: '2019-11-8 14:30',
						address: '高新区',
						people: '2'
					},
					{
						url: '../../static/banner.png',
						title: '测试活动',
						time: '2019-11-8 14:30',
						address: '高新区',
						people: '2'
					},
					{
						url: '../../static/banner.png',
						title: '测试活动',
						time: '2019-11-8 14:30',
						address: '高新区',
						people: '2'
					},
				]
			}
		},
		onLoad: {
			// var _self = this;
			// this.getList();
		},
		methods: {
			getList() {
				uni.request({
					url: '',
					success: (res) =>{
						console.log(res);
						this.list = res.data.data
					}
				})
			}
		}
	}
</script>

<style lang="scss">
	.enroll-page {
		padding: 0 22rpx;
	}
	.enroll {
		width: 100%;
		height: 500rpx;
		margin-top: 10px;
		image {
			width: 100%;
			height: 300rpx;
		}
	}
	.enroll-ent {
		margin-top: 8px;
		padding-bottom: 10px;
		border-bottom: 1px dashed #ccc;
		p {
			font-size: $font-sm + 5upx;
			color: #ccc;
			text {
				color: black;
			}
		}
	}
</style>
