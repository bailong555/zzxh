<template>
	<view>
		<view class="public_customer center">
			<view class="PC_input spaceBetween">
				<view class="input">
					<view class="PC_Pic PC_LeftPic">
					</view>
					<input class="PC_input_text" placeholder="请输入搜索的关键词"/>
				</view>
				<button type="primary" class="btn">搜索</button>
			</view>
		</view>
	</view>
</template>
<script>
	export default {
		data(){
			return {
				// customerRouterUrl:"../../common/find-customer/choose-customer",
				customerInfoShow:''
			}
		},
		props:{
			placeHolder: {
				type: String,
			},
		},
		methods:{
			chooseCustomerTap(){
				uni.navigateTo({
				    url: this.customerRouterUrl,
					success() {
						// console.log(111)
					},
					fail() {
						// console.log(22)
					}
				});
			},
			
		},
	}
</script>

<style lang="scss" scoped>
	.public_customer {
	 	height: 100upx;
	 	box-shadow: 1px 1px 1px 1px #ccc;
	}
	.PC_input{
	 	width: 700upx;
	 	height: 60upx;
	 	overflow: hidden;
	 	padding-top: 10px;
	 	margin-left: 13px;
	}
	.input {
		width: 380rpx;
	 	height: 100%;
	 	background: #ccc;
	 	float: left;
	}
	 .PC_input_text{
	 	width: 380upx;
	 	height: 60upx;
	 	border:none;
	 	color: #323232;
		padding-left: 30px;
	 	font-size: $font-sm + 5upx;
		background: url(../../static/nav_search.png) no-repeat;
	}
	.btn {
	 	width: 120rpx;
	 	height: 100%;
	 	line-height: 60rpx;
	 	font-size: $font-sm + 5upx;
	 	float: left;
	 	background: red;
	}
	.content1{
	     height: 150upx;
	 }
	 
	 page{
	     background-color: #FFFFFF;
	 }
	 /* 搜索框 */
	 .search-ico, .search-ico-1{
	     width: 40upx;
	     height: 40upx;
	 }
	 .search-text{
	     font-size: 14px;
	     background-color: #FFFFFF;
	     height: 60upx;
	     width: 480upx;
	 }
	 .search-block{
	     display: flex;
	     flex-direction: row;
	     padding-left: 60upx;
	     position: relative;
	     top: -32upx;
	 }
	 .search-ico-wapper{
	     background-color: #FFFFFF;
	     display: flex;
	     flex-direction:column;
	     justify-content: center;
	     padding: 0upx 0upx 0upx 40upx;
	     border-bottom-left-radius:18px;
	     border-top-left-radius: 18px;
	 }
	 .search-ico-wapper1{
	     background-color: #FFFFFF;
	     display: flex;
	     flex-direction:column;
	     justify-content: center;
	     padding: 0upx 40upx 0upx 0upx;
	     border-bottom-right-radius:18px;
	     border-top-right-radius: 18px;
	 }
	 .shadow{
	     width: 458upx;
	     height: 60upx;
	     border-radius:18px;
	     -moz-box-shadow:0 0 10px #e6e6e6;
	     -webkit-box-shadow:0 0 10px #e6e6e6;
	     box-shadow:0 0 10px #e6e6e6;
	     position: relative;
	     top: -90upx;
	     left: 60upx;
	 }
</style>
