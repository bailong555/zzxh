<template>
	<view>
		<view class="login-head-l1"  @click="btnClick">
			<text :class="{'color':1 == anchorIndex}" data-index="1">活动详情展示</text>
			<text :class="{'color':2 == anchorIndex}" data-index="2">会员互动展示</text>
		</view>
		<view class="main" v-for="item in enrollList" :key="item.index">
			<view class="forum">
				<p>{{ item.title1 }}</p>
				<p>发布时间:<text>{{ item.time1 }}</text>作者:<text>管理员</text></p>
			</view>
			<view class="enroll">
				<image :src=" item.url1 "></image>
				<view class="enroll-ent">
					<p>会议主题：<text>{{ item.title }}</text></p>
					<p>时间：<text>{{ item.time }}</text></p>
					<p>地址：<text>{{ item.address }}</text></p>
					<p>已报名：<text>{{ item.people }}人</text></p>
					<p>押金：<text>{{ item.price }}人</text></p>
				</view>
			</view>
			<view class="main-div">
				<view class="describe">
					<p>{{ item.title2 }}</p>
					<view class="describe-div1">
						<image :src=" item.url2 "></image>
						<p>{{ item.conent }}</p>
						<image :src=" userStatus.url " class="describe-img"
						@click="interact"></image>
					</view>
					<view class="describe-div2">
						<image :src=" item.url3 "></image>
						<p>{{ userStatus.remarks }}
							<p>{{ userStatus.conent }}</p>
						</p>
					</view>
				</view>
			</view>
			<view class="footer">
				<image src="../../static/code_pic_qr code.png"/>
				<view class="login-head-l2"  @click="perClick">
					<text :class="{'backgroundColor':1 == perIndex}" data-index="1">签到</text>
					<text :class="{'backgroundColor':2 == perIndex}" data-index="2">报名</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data () {
			return {
				// 用户选择
				 anchorIndex:1,
				 perIndex:1,
				 //备注
				 userStatus: {
					 url: '../../static/activity_icon_add.png',
					 remarks: '备注',
					 conent: '郑州女企协会会员代表大会要求全体会员出席，请您调整好自己的时间!'
				 },
				//活动详情
				enrollList: [
					{
						title1: '【开展非公企业党建论坛】',
						time1: '2019-11-8 14：30',
						url1: '../../static/banner.png',
						title: '测试活动',
						time: '2019-11-8 14：30',
						address: '高新区',
						people: '2',
						title2: '【活动描述】',
						url2: '../../static/banner.png',
						url3: '../../static/banner.png',
						conent: '123',
						price: '20'
					}
				]
			}
		},
		methods: {
			//点击按钮变色
			btnClick(e){
				if(e.target.dataset.index != 2 ){
				    this.anchorIndex = 1;
				}else{
				    //获取当前点击事件的下标
				    this.anchorIndex =  e.target.dataset.index
				}
			},
			perClick(e) {
				if(e.target.dataset.index != 2){
					this.perIndex = 1;
				} else {
					this.perIndex = e.target.dataset.index
				}
			},
			//跳转互动页面
			interact() {
				uni.navigateTo({
					url: '/pages/myhome/interact'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.color{
		height: 72rpx;
		line-height: 60rpx;
		color:#ff5112;
		border-bottom:1px solid blue;
	}
	.backgroundColor {
		height: 70rpx;
		line-height: 70rpx;
		color:#ff5112;
		background: red;
	}
	.login-head-l1{
		width: inherit;
		height: 72rpx;
		line-height: 72rpx;
		cursor: pointer;
		text-align: center;
		border-bottom: 1px solid #ccc;
		text:nth-child(1) {
			margin-right: 100rpx;
		}
	}
	.login-head-l1 text{
	    font-size: $font-sm + 5upx;
	    padding: 15rpx 20px;
	    color: black;
		margin-top: 5px;
	}
	.login-head-l1:before{
	    content:'';
	    height: 35px;
	    margin-left: 5px;
	}
	.main {
		padding: 22rpx;
	}
	.forum {
		p {
			width: 100%;
			text-align: center;
			font-size: $font-sm + 5upx;
			margin-top: 10rpx;
		}
		p:nth-child(1) {
			font-size: $font-sm +15upx;
		}
	}
	.enroll {
		width: 100%;
		margin-top: 10px;
		border-top: 1px dashed #ccc;
		border-bottom: 1px dashed #ccc;
		padding: 15rpx 0 15rpx 0;
		image {
			width: 100%;
			height: 300rpx;
		}
	}
	.enroll-ent {
		margin-top: 8px;
		padding-bottom: 10px;
		p {
			font-size: $font-sm + 5upx;
			color: #ccc;
			text {
				color: black;
			}
		}
	}
	.enroll-ent p:nth-of-type(5) {
		background: url(../../static/image_arrow_home.png) no-repeat right;
		background-size: 8px;
	}
	.main-div {
		margin-top: 35rpx;
	}
	.describe {
		width: 100%;
		p {
			width: 100%;
			text-align: center;
			font-size: $font-sm + 15upx;
			margin-top: 10rpx;
		}
	}
	.describe-div1 {
		position: relative;
	}
	.describe-div1 .describe-img {
		width: 150rpx;
		height: 150rpx;
		position: absolute;
		top: 50%;
		right: 5%;
	}
	.describe-div1,
	.describe-div2 {
		width: 100%;
		margin-top: 15rpx;
		p {
			text-align: left;
			font-size: $font-sm + 5upx;
		}
		image {
			width: 100%;
			height: 300rpx;
		}
	}
	.footer {
		width: 100%;
		height: 500rpx;
		text-align: center;
		margin-top: 55rpx;
		image {
			width: 300rpx;
			height: 300rpx;
		}
	}
	.login-head-l2{
		height: 70rpx;
		line-height: 70rpx;
		cursor: pointer;
		text-align: center;
		margin-top: 30rpx;
		text:nth-child(1) {
			margin-right: 100rpx;
		}
	}
	.login-head-l2 text{
	    font-size: $font-sm + 5upx;
	    padding: 8px 40px;
	    color: black;
		margin-top: 5px;
	}
</style>
