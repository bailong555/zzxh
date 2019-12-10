<template>
    <view>
        <view class="input-box">
			<view class="login">
				<p>登录</p>
			</view>
            <view class="input-item">
                <view class="input-label">手机号</view>
				<view class="input-body">
					<input v-model="phone" maxlength="11" type="number" placeholder="请输入手机号" class="input" >
				</view>
            </view>
            <view class="input-item">
				<view class="input-label">密码</view>
				<view class="input-body">
					<input :type="passwordType" v-model="password" :password="isHidePassword?true:false" style="margin-right: 50upx;" placeholder="请输入密码" maxlength="20"  class="input" />
					<image @click="isHidePasswordClick" class="eye" src="../../static/nav.png"></image>
				</view>
            </view>
            <view class="select">
				<navigator url="/pages/forget-pwd/forget-pwd" hover-class="none">忘记密码？</navigator>
                <navigator url="/pages/register/register" hover-class="none" style="color: #FF0060;">马上注册</navigator>
            </view>
        </view>
        <button class="button" @tap="submit">登录</button>
    </view>
</template>
<script>
	import {checkPhone,checkPwd} from "@/common/common.js"
	export default {
		data() {
			return {
				passwordType: 'password',
				isHidePassword:true,
				phone:"",
				password:""
			};
		},
		onLoad() {
			var self = this;
		},
		methods: {
			isHidePasswordClick(){
				this.isHidePassword=!this.isHidePassword
			},
			//登录
			submit() {
				if (this.phone.length <= 0) {
					uni.showToast({
						icon: 'none',
						title: '请输入手机号'
					});
				    return;
				}
				if (this.pwd.length <= 0) {
					uni.showToast({
						icon: 'none',
						title: '请输入密码'
					});
					return;
				}
				uni.request({
					url: '',
					data: {
						phone: this.phone,
						pwd: this.pwd
					},
					success: (res) => {
						let list=JSON.stringify(res.data);
						console.log("返回数据状态:" + list);
						if(list=="[]"){
							uni.showToast({
							    icon: 'none',
							    title: '用户名或密码错误'
							});
						    return;
						}
						//缓存手机号和密码
						if(res.data == 1) {
							uni.setStorageSync('HCuname', self.phone);
							uni.setStorageSync('HCpwd', self.pwd);
							uni.setStorageSync('islogin', true);//登录状态
							//跳转首页
							uni.navigateTo({
							    url: '/pages/index/index'
							});
						}
						uni.showToast({
							icon: 'none',
							title: '登录成功'
						})
					},
					fail: () => {
						uni.showToast({
							icon: 'none',
							title: '网络异常,请稍后重试'
						})
					}
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	button::after{
		border: none;
	}
	.login {
		width: 100%;
		height: 150rpx;
		line-height: 150rpx;
		p {
			font-size: $font-sm + 15upx;
		}
	}
	.input-box {
		padding: 50upx;
		font-size: 30upx;
		.input-item {
			display: flex;
			background: white;
			border-bottom: 1upx solid #eeeeee;
			line-height: 100upx;
			height: 100upx;
			.input-label {
				width: 150upx;
			}
			.input-body{
				position: relative;
				height: 100upx;
				width: calc(100% - 150upx);
				.input {
					line-height: 90upx;
					height: 90upx;
					position: relative;
					font-size: 28upx;
					border: none;
					outline: none;
				}
				.eye{
					position: absolute;
					height: 50upx;
					width: 50upx;
					right: 0;
					top: 50%;
					transform: translateY(-50%);
				}
				.btn-code{
				    position: absolute;
				    right: 0upx;
				    top:50%;
				    transform: translateY(-50%);
					background: none;
					color: #205592;
					width: 160upx;
					font-size: 24upx;
					box-sizing: border-box;
					text-align: right;
					padding: 0;
					height: 100upx;
					line-height: 100upx;
				}
			}
			
		}
		.select {
			padding-top: 40upx;
			display: flex;
			justify-content: space-between;
			color: #003B67;
		}
	}
	.button{
		margin:0 30upx;
		background: #FF0060;
		border-radius:50upx;
		line-height: 80upx;
		height: 80upx;
		color: white;
		font-size: 32upx;
	}
</style>
