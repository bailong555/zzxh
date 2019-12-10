<template>
	<view class="content">
		<view class="head">
			<image src="../../static/shopping/indent/nav_Back.png"></image>
			<text>收货地址</text>
		</view>
		<view class="nav">
			<view class="top">
				<text>星海</text>
				<text style="left:-10%;">01234567891</text>
				<text>河南省郑州市</text>
			</view>
			<view class="bottom">
				<image class="i1" src="../../static/list_Button_Selected.png"></image>
				<text class="a" style="color:#FF0E69;">设为默认</text>
				<image class="i2" src="../../static/list_Button_Edit.png"></image>
				<text class="b">编辑</text>
				<image class="i3" src="../../static/list_Button_Delete.png"></image>
				<text class="c">删除</text>
			</view>
		</view>
		<view class="nav">
			<view class="top">
				<text>星海</text>
				<text style="left:-10%;">01234567891</text>
				<text>河南省郑州市</text>
			</view>
			<view class="bottom">
				<image class="i1"src="../../static/shopping/take/list_Button.png"></image>
				<text class="a">设为默认</text>
				<image class="i2" src="../../static/list_Button_Edit.png"></image>
				<text class="b">编辑</text>
				<image class="i3" src="../../static/list_Button_Delete.png"></image>
				<text class="c">删除</text>
			</view>
		</view>
		<view class="nav">
			<view class="top">
				<text>星海</text>
				<text style="left:-10%;">01234567891</text>
				<text>河南省郑州市</text>
			</view>
			<view class="bottom">
				<image class="i1"src="../../static/shopping/take/list_Button.png"></image>
				<text class="a">设为默认</text>
				<image class="i2" src="../../static/list_Button_Edit.png"></image>
				<text class="b">编辑</text>
				<image class="i3" src="../../static/list_Button_Delete.png"></image>
				<text class="c">删除</text>
			</view>
		</view>
		<button class="toRedact" @click="toRedact" type="warn">添加地址</button>
	</view>
</template>

<script>
	export default{
		data(){
			return{
			}
		},
		methods:{
			toRedact(){
				uni.navigateTo({
					url:'../redact/redact'
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
		.head{
			width: 100%;
			height: 100upx;
			image{
				width: 60upx;
				height:60upx;
				border:1upx dashed #000;
				margin: 30upx;
			}
			text{
				position: relative;
				top:-45%;
				font-weight: 800;
			}
		}
		.nav{
			margin: 20upx auto;
			width: 90%;
			height: 236upx;
			line-height: 200%;
			background: #FFFFFF;
			border-radius:10upx;
			.top{
				width: 100%;
				height: 65%;
				border-bottom:1upx dashed #E9E9E9;
			}
			text{
				display: inline-block;
				width: 35%;
				height:30%;
				position: relative;
				top:5%;
				left:5%;
				font-size: 32upx;
			}
			image{
				position: relative;
				top:-30%;
				left:45%;
			}
			.bottom{
				width: 100%;
				height: 35%;
				position: relative;
				image{
					width:40upx;
					height:40upx;
					position: absolute;
					top:10%;
					left:0;
				}
				.i2{
					left:50%;
				}
				.i3{
					left:75%;
				}
				text{
					position: absolute;
					top:10%;
					left:12%;
					font-size:30upx;
				}
				.b{
					left:62%;
				}
				.c{
					left:87%;
				}
			}
		}
		.toRedact{
			width: 100%;
			height:5%;
			position: absolute;
			bottom:0;
			text-align: center;
			line-height: 200%;
			font-size:40upx;
			color: #fff;
		}
	}
</style>
