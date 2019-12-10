<template>
	<view>
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
					<text @tap="show('QSPopup2')" :class="{'backgroundColor':2 == perIndex}" data-index="2">报名</text>
				</view>
			</view>
		</view>
		<QSPopup ref="QSPopup2" type="fadeInUp">
			<view class="content">
				<view class="content-div" v-for="item in list" :key="item.id">
					<p>{{ item.title }}</p>
					<p>活动押金<text>￥{{ item.price }}</text></p>
					<view class="price">
						<p>合计<text>￥{{ item.price }}</text></p>
						<button>支付</button>
					</view>
				</view>
			</view>
		</QSPopup>
	</view>
</template>

<script>
	import QSPopup from '../../components/QS-popup/QS-popup.vue';
	export default {
		components:{QSPopup},
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
				],
				list: [
					{
						title: '首次参与活动免费,之后会员押金可退,预备会员则不退押金',
						price: '20'
					}
				]
			}
		},
		methods: {
			//点击按钮变色
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
			},
			//支付弹出层
			show(ref) {
				this.$refs[ref].show();
			}
		}
	}
</script>

<style lang="scss" scoped>
	.backgroundColor {
		height: 70rpx;
		line-height: 70rpx;
		color:#ff5112;
		background: #FF0060;
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
	//弹出层
	.content {
		height: 500rpx;
		width: 100%;
		background-color: white;
		border-radius: 10rpx;
		position: relative;
	}
	.content p {
		font-size: $font-sm;
	}
	.content .content-div {
		padding: 50rpx 35rpx 0 35rpx;
	}
	.content-div p:nth-of-type(2) {
		width: 80%;
		height: 80rpx;
		border: 1px solid #FF0060;
		line-height: 80rpx;
		padding: 0 22rpx;
		margin: 0 auto;
		margin-top: 30px;
		border-radius: 5px;
	}
	.content-div p:nth-of-type(2) text {
		float: right;
		color: #FF0060;
	}
	.price {
		width: 98%;
		height: 80rpx;
		line-height: 100rpx;
		position: absolute;
		bottom: 0;
		display: flex;
		justify-content: space-between;
	}
	.price p {
		width: 60%;
		text {
			color: #FF0060;
			padding-left: 22rpx;
		}
	} 
	.price button {
		width: 40%;
		height: 80rpx;
		line-height: 80rpx;
		background: #FF0060;
		color: #fff;
		font-size: $font-sm;
	}
</style>
