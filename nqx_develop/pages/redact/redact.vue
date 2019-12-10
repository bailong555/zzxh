<template>
	<view class="content">
		<view class="aaa">
			<view class="head">
				<image src="../../static/shopping/indent/nav_Back.png"></image>
				<text>编辑地址</text>
			</view>
			<view class="redact">
				<view class="con">
					<text>收件人</text>
					<input type="text" placeholder="请填写收件人姓名" />
				</view>
				<view class="con">
					<text>手机号码</text>
					<input type="text" placeholder="请填写收件人手机号" />
				</view>
				<view class="con">
					<text>所在地区</text>
					<input type="text" placeholder="省份 城市 地区 街道" />
				</view>
				<view class="con" style="border:none">
					<text>详细地址</text>
					<input type="text" placeholder="道路、小区、单元室、门牌等" />
				</view>
			</view>
		</view>
		<button type="primary" class="btn" @click="toDev">完成</button>
	</view>
</template>

<script>
	export default{
		data(){
			return{
			}
		},
		methods:{
			toDev(){
				uni.navigateTo({
					url:'./redact-dev'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
	.content{
		width: 100%;
		height: 1600upx;
		background: #F5F5F5;
		position: relative;
		image{
			width: 60upx;
			height:60upx;
			border:1upx dashed #000;
			margin: 30upx;
		}
		.aaa{
			height:600upx;
			background: #FFFFFF;
			.head{
				width: 100%;
				height:20%;
				text{
					position: relative;
					top:-45%;
					font-weight: 800;
				}
			}
			.redact{
				width: 100%;
				height:85%;
				.con{
					width: 90%;
					height: 12%;
					margin:20upx auto;
					border-bottom:1upx solid #000;
					text{
						font-size: 30upx;
						color:#545454;
						float: left;
					}
					input{
						width:80%;
						margin-left:25%;
						font-size:26upx;
					}
				}
			}
		}
		.btn{
			margin-top: 10%;
			width: 90%;
			height:6%;
			text-align: center;
			border-radius: 50upx;
			background:#CCCCCC;
		}
	}
</style>
