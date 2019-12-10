<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	/*每个页面公共css */
	uni-swiper .uni-swiper-dot-active {
		background: #fff;
	}
	uni-image>img {
		opacity: 1;
    }
	uni-button {
		border-radius: 0;
	}
	.uni-drawer__content {
		width: 500rpx;
	}
	.uni-page-head-search-placeholder-center {
		left: 17%;
	}
	uni-app, uni-page-head {
		height: 43px;
	}
	.PC_input_text {
		text-align: left;
	}
	.QS_fadeInUp.show {
		width: 100%;
	}
</style>
