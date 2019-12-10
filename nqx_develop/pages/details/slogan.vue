<template>
	<view class="content">
		<view class="slogan">
			<p>企业宣传语<text>重新上传</text></p>
		</view>
		<view class="comment">
		    <textarea placeholder="" v-model="content"></textarea>
		</view>
		<view class="btn" @click="slogned">
			立即提交
		</view>
	</view>
</template>

		
<script>
	export default {
		data() {
			return {
				//宣传语
				content: ''
			}
		},
		methods: {
			//提交宣传语
			slogned() {
			    if (this.content.length < 1) {
			       uni.showModal({ content: '内容不能为空', showCancel: false, });
			       return;
			    } 
				uni.showLoading({title:'发布中'});
				
			}
		}
	}
</script>

<style lang="scss" scoped>
	.slogan {
		width: 100%;
		height: 50rpx;
		font-size: $font-sm + 5upx;
		text {
			float: right;
			color: red;
		}
	}
	.content {
		min-height: 800px;
		padding: 15px;
	}
	.comment {
		border: 1px solid #ccc;
		padding:  22rpx;
	    textarea {
			width: 100%;
			height: 230rpx;
			margin-top: 0;
	    }      
	}
	.btn {
		width: 100%;
		height: 70rpx;
		color: #fff;
		background: #FF106A;
		font-size: 14px;
		text-align: center;
		line-height: 70rpx;
		margin: 0 auto;
		margin-top: 15px;
		border-radius: 5px;
	}
</style>
