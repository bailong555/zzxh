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
				<view>
					<button class="bouun" type="primary" @tap="show('QSPopup6')">筛选</button>
					<QSPopup ref="QSPopup6" type="fadeInLeft">
						<view class="content" style="height: 100vh;width: 500rpx;background-color: white;border-top-left-radius: 10rpx;border-bottom-left-radius: 10rpx;">
							<view class="layer">
								<view class="layer-div">
								<!-- 行业划分 -->
									<view class="layer-div1">
										<p>{{ userList.trade }}</p>
										<view class="layer-div-div1" v-for="item in list" :key="item.index">
											<view>{{ item }}</view>
										</view>
									</view>
								<!-- 区域划分 -->
									<view class="layer-div2">
										<view class="area">
										<p>{{ userList.area }}</p>
									</view>
									<view class="age">
										<p>{{ userList.age }}</p>
										<view class="login-head-l1"  @click="btnClick">
											<text :class="{'color':1 == anchorIndex}" data-index="1">升序</text>
											<text :class="{'color':2 == anchorIndex}" data-index="2">降序</text>
										</view>
									</view>
								</view>
								<!-- 选择 -->
								<view class="login-head-l2"  @click="perClick">
									<text :class="{'backgroundColor':1 == perIndex}" data-index="1">重置</text>
									<text :class="{'backgroundColor':2 == perIndex}" data-index="2">完成</text>
								</view>
							</view>
						  </view>
						</view>
					</QSPopup>
				</view>
			</view>
		</view>
	</view>
</template>
<script>
	import QSPopup from '../../components/QS-popup/QS-popup.vue';
	export default {
		components: {
			QSPopup
		},
		data(){
			return {
				//用户选择
				anchorIndex: 1,
				perIndex: 1,
				//弹出层
				showRight: false,
				customerInfoShow:'',
				//行业划分
				list: [
					'电子信息',
					'新材料',
					'生物及医药',
					'汽车制造业',
					'现代食品制造'
				],
				userList: {
					trade: '按照行业划分',
					area: '区域划分',
					age: '法人年龄'
				},
				//查询关键字
				query: '',
			}
		},
		props:{
			placeHolder: {
				type: String,
			},
		},
		methods:{
			//点击按钮变色
			btnClick(e){
				if(e.target.dataset.index != 2 ){
				    this.anchorIndex = 1;
				}else{
				    //获取当前点击事件的下标
				    this.anchorIndex =  e.target.dataset.index
				}
			},
			perClick(e){
				if(e.target.dataset.index != 2 ){
				    this.perIndex = 1;
				}else{
				    //获取当前点击事件的下标
				    this.perIndex =  e.target.dataset.index
				}
			},
			//弹出层
			show(ref) {
				this.$refs[ref].show();
			},
			//搜索
			remoteMethod () { 
			    var keyword = this.query
			    if(keyword) {
			        ocation.href = "#/index?keyword="+keyword;
			    }else {
			        alert('请输入搜索内容')
			    }
			    var keyword = getParamsByUrl (location.href,'keyword')
			    function getParamsByUrl (url,name) {
			        var params=url.substr(url.indexOf('?')+1);
			        var param=params.split();
			        for(var i=0;i<param.length;i++){
			            var current=param[i].split('=');
			            if(current[0]==name){
			                return current[1]
			            }
			        }
			            return null;
			    }
				uni.request({
					url: '',
					data: '',
					success: (res) => {
						console.log(res)
						if (res.status == 200) {
						    this.list = res.data.data
						    console.log(this.list);
						} else {
						    alert('获取列表失败')
						}
					}
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.bouun {
		width: 30px;
		height: 30px;
	}
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
		padding-left: 30px;
		border:none;
		color: #323232;
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
	.color {
		height: 72rpx;
		line-height: 60rpx;
		color:#ff5112;
		background: red;
	}
	.backgroundColor {
		height: 72rpx;
		line-height: 72rpx;
		color:#ff5112;
		background: red;
	}
	.login-head-l1{
		width: inherit;
		height: 72rpx;
		line-height: 72rpx;
		cursor: pointer;
		text-align: left;
		margin-top: 30rpx;
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
	.login-head-l2{
		width: 100%;
		height: 72rpx;
		line-height: 72rpx;
		cursor: pointer;
		text-align: left;
		margin-top: 30rpx;
		position: absolute;
		top: 80%;
		text:nth-child(1) {
		 	margin-right: 10rpx;
	    }
	}
	.login-head-l2 text{
		padding: 15rpx 80rpx;
	    font-size: $font-sm + 5upx;
	    color: black;
		margin-top: 5px;
	}
	.ptore {
		width: 50%;
		height: 150rpx;
		float: left;
	}
	.layer {
		width: 100%;
		height: 90%;
		padding-top: 10%;
	}
	.layer-div {
		margin-top: 50rpx;
		padding: 22rpx;
		height: 100%;
		position: relative;
		.layer-div1 {
			height: 300rpx;
			border-bottom: 1px solid #ccc;
			p {
			   font-size: $font-sm + 5upx;
			   color: #ccc;
			}
		}
	}
	.layer-div-div1 {
		width: 100%;
		view {
			float: left;
			height: 30px;
			line-height: 30px;
			color: #fff;
			background: #bbb;
			font-size: $font-sm;
			margin: 20rpx 10rpx 0 0;
			padding: 0 12rpx;
		}
	}
	.layer-div2 {
		height: 300rpx;
		border-bottom: 1px solid #ccc;
		p {
			font-size: $font-sm+5upx;
			color: #ccc;
		}
	}
	.age {
		button {
			width: 150rpx;
			height: 50rpx;
			line-height: 50rpx;
			font-size: $font-sm+5upx;
			margin-top: 15px;
			float: left;
			border: none;
			color: #fff;
			background: #ccc;
		}
	}
	.nav_active {
	    background: red;
	}
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
		font-size: $font-sm + 5upx;
	}
	.btn {
		width: 120rpx;
		height: 100%;
		line-height: 60rpx;
		font-size: $font-sm + 5upx;
		float: left;
		background: red;
	}
	.img {
		width: 30px; 
		height: 30px; 
	 	margin-left: 20px;
    }
</style>
