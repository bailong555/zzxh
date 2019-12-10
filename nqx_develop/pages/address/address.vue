<template>
	<view class="content b-t">
		<view class="list b-b" v-for="(item, index) in addressList" :key="index" @click="checkAddress(item)">
			<view class="wrapper">
				<view class="u-box">
					<text class="name">{{item.name}}</text>
					<text class="mobile">{{item.mobile}}</text>
				</view>
				<view class="address-box">
					<!-- <text v-if="item.default" class="tag">默认</text> -->
					<text class="address">{{item.addressName}} {{item.area}}</text>
				</view>
			</view>
			<view class="yticon">
				<p><text>设为默认</text></p>
				<view class="yticon-div">
					<p><text>编辑</text></p>
					<p><text>删除</text></p>
				</view>
			</view>
		</view>
		<button class="add-btn" @click="addAddress('add')">添加地址</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				source: 0,
				addressList: [
					{
						name: '刘晓晓',
						mobile: '18666666666',
						addressName: '贵族皇仕牛排(东城店)',
						address: '北京市东城区',
						area: 'B区',
						default: true
					},{
						name: '刘大大',
						mobile: '18667766666',
						addressName: '龙回1区12号楼',
						address: '山东省济南市历城区',
						area: '西单元302',
						default: false,
					}
				]
			}
		},
		onLoad(option){
			console.log(option.source);
			this.source = option.source;
		},
		methods: {
			//选择地址
			checkAddress(item){
				if(this.source == 1){
					//this.$api.prePage()获取上一页实例，在App.vue定义
					this.$api.prePage().addressData = item;
					uni.navigateBack()
				}
			},
			addAddress(type, item){
				uni.navigateTo({
					url: `/pages/address/addressManage?type=${type}&data=${JSON.stringify(item)}`
				})
			},
			//添加或修改成功之后回调
			refreshList(data, type){
				//添加或修改后事件，这里直接在最前面添加了一条数据，实际应用中直接刷新地址列表即可
				this.addressList.unshift(data);
				
				console.log(data, type);
			}
		}
	}
</script>

<style lang='scss' scoped>
	page{
		padding-bottom: 120upx;
	}
	.content{
		position: relative;
		min-height: 1200px;
		background: #F5F5F5;
		padding: 23rpx;
	}
	.list{
		/* display: flex;
		align-items: center; */
		background: #fff;
		position: relative;
		margin-bottom: 15px;
		border-radius: 15px;
	}
	.wrapper{
		display: flex;
		flex-direction: column;
		flex: 1;
		padding: 20upx 30upx;
		border-bottom: 1px solid #ccc;
	}
	.address-box{
		display: flex;
		align-items: center;
		margin-top: 8px;
		.tag{
			font-size: 24upx;
			color: $base-color;
			margin-right: 10upx;
			background: #fffafb;
			border: 1px solid #ffb4c7;
			border-radius: 4upx;
			padding: 4upx 10upx;
			line-height: 1;
		}
		.address{
			font-size: 30upx;
			color: $font-color-dark;
		}
	}
	.u-box{
		font-size: 28upx;
		color: $font-color-light;
		margin-top: 8px;
		.name{
			margin-right: 30upx;
		}
	}
	.yticon {
		width: 93%;
		height: 35px;
		padding: 15px 22rpx 0 22rpx;
		font-size: $font-sm + 5upx;
		p {
			width: 150rpx;
			background: url(../../static/list_Button_Selected.png) no-repeat;
			text-align: right;
			float: left;
		}
		.yticon-div {
			float: right;
			p {
				width: 100rpx;
			}
			p:nth-of-type(1) {
				background: url(../../static/list_Button_Edit.png) no-repeat;
				margin-right: 80rpx;
			}
			p:nth-of-type(2) {
				background: url(../../static/list_Button_Delete.png) no-repeat;
			}
		}
	}
	.icon-bianji{
		display: flex;
		align-items: center;
		height: 80upx;
		font-size: 40upx;
		color: $font-color-light;
	}
	
	.add-btn{
		position: fixed;
		left: 30upx;
		right: 30upx;
		bottom: 16upx;
		z-index: 95;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 690upx;
		height: 80upx;
		font-size: 32upx;
		color: #fff;
		background-color: $base-color;
		border-radius: 10upx;
		box-shadow: 1px 2px 5px rgba(219, 63, 96, 0.4);		
	}
</style>
