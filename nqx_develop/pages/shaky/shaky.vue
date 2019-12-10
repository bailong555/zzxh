<template>
	<view>
		<view class="activity-div">
			<QSPopup ref="QSPopup" v-show="isShow">
				<view class="content" style="height: 300rpx;width: 300rpx;background-color: white;border-radius: 10rpx;">
					<p>您还没有登录</p>
					<p><navigator url="/pages/login/login">去登录</navigator></p>
				</view>
			</QSPopup>
				<view class="activity-ver" @tap="show('QSPopup')" v-for="item in shakyList" :key="item.id">
					<navigator url="/pages/myhome/myhome?item.id" class="router">
						<p>{{ item.time }}</p>
						<view class="activity-ver-div">
							<image :src=" item.url "  style="z-index: -1"/>
							<p>{{ item.title }}</p>
						</view>
					</navigator>
				</view>
		</view>
	</view>
</template>

<script>
	import QSPopup from '../../components/QS-popup/QS-popup.vue';
	export default {
		components:{QSPopup},
		data () {
			return {
				isShow: false,
				shakyList: [
					{
						time: '2019-11-8 12:7',
						url: '../../static/banner.png',
						title: '测试活动'
					},
					{
						time: '2019-11-8 12:7',
						url: '../../static/banner.png',
						title: '测试活动'
					}
				]
			}
		},
		onLoad() {
			var self = this;
			self.getShaky();
			self.changeid()
		},
		methods: {
			//活动列表
			getShaky() {
				uni.request({
					url: '',
					dataType: 'json',
					success: (res) => {
						console.log(res)
						if(res.data == 1) {
							this.shakyList = res.data.data
							console.log(this.shakyList)
						}
					}
				})
			},
			changeid(){
			 	self.islogin = uni.setStorageSync('islogin', true);//登录状态
			 	var upname = uni.setStorageSync('HCuname'); //手机号
				if(self.is_login==true || self.is_login=='true') {
			 		this.isShow = false;
			 	} else {
			 		this.isShow = true;
			 	}
			},
			//弹出层
			show(ref) {
				this.$refs[ref].show();
			}
		}
	}
</script>

<style lang="scss" scoped>
	//弹出层
	button{
		margin: 20rpx;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.content p {
		font-size: 16px;
		margin-top: 15px;
	}
	.content p:nth-of-type(2) {
		color: #FF0060;
	}
//头部
.router {
	display: block;
	width: 100%;
	height: 100%;
	// margin-top: 15px;
}
.activity-div {
	padding: 0 22rpx; 
	.activity-ver {
		width: 100%;
		height: 210px;
		margin-top: 15px;
		p { 
			width: 100%;
			height: 30px;
			line-height: 30px;
			text-align: center;
			font-size: $font-sm + 5upx;
		}
		.activity-ver-div {
			width: 100%;
			height: 180px;
			border-radius: 5px;
			box-shadow: 1px 1px 1px 1px #ccc;
			image {
				width: 100%;
				height: 150px;
			}
			p {
				width: 90%;
				height: 20px;
				background: #fff;
				text-align: left;
				padding-left: 22rpx;
				line-height: 20px;
			}
		}
	}
}
</style>
