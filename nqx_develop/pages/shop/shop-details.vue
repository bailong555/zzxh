<template>
	<view>
		<view class="shop-details" v-for="item in list" :key="item.id">
			<image src="../../static/shop_pic02.png"></image>
			<!-- 商品详情 -->
			<view class="main">
				<view class="details-integral">
					<p>抢购价:<text>￥{{ item.price }}</text></p>
					<view class="div">
						<text class="spn1">{{ item.integral }}</text><text class="spn2">积分抵{{ item.ptop }}</text>
					</view>
					<h5>{{ item.title }}</h5>
					<p>{{ item.conent }}</p>
				</view>
				<view class="details-div">
					<p class="details-p"><text>{{ details.shop }}</text></p>
					<view class="details-div-main" v-for="item in detailsList" :key="item.id">
						<p>品牌<text>{{ item.name }}</text></p>
						<p>产量<text>{{ item.address }}</text></p>
						<p>净含量<text>{{ item.ptre }}</text></p>
						<p>包装方式<text>{{ item.pftre }}</text></p>
					</view>
				</view>
			</view>
			<view class="details-div2">
				<image src="../../static/banner.png"/>
			</view>
			<!-- 猜你喜欢 -->
			<view class="details-like">
				<p class="like-p">{{ details.liked }}</p>
				<view class="details-like-div" v-for="item in likeList" :key="item.id">
					<view class="liked-shop">
						<image :src=" item.url "/>
						<h5>{{ item.title }}</h5>
						<p>{{ item.conent }}</p>
						<p>￥<text>{{ item.price }}</text><text class="spn">{{ item.recom }}</text></p>
					</view>
				</view>	
			</view>
		</view>
		<view>
			<button type="primary" @tap="show('QSPopup2')" class="btn">立即购买</button>
			<QSPopup ref="QSPopup2" type="fadeInUp">
				<view class="content">
					<view class="a-t">
						<image src="https://gd3.alicdn.com/imgextra/i3/0/O1CN01IiyFQI1UGShoFKt1O_!!0-item_pic.jpg_400x400.jpg"></image>
						<view class="right">
							<h5 style="margin-top: 5px;font-size: 12px;color:#1E1E1E">碧螺春云雾新绿茶罐装明前新茶</h5>
							<text class="price">¥50</text>
							<text class="stock">库存：188件</text>
							<view class="selected">
								<!-- 已选： -->
								<text class="selected-text" v-for="(sItem, sIndex) in specSelected" :key="sIndex">
									{{sItem.name}}
								</text>
							</view>
						</view>
					</view>
					<view v-for="item in specList" :key="item.id" class="attr-list">
						<text>{{item.name}}</text>
						<view class="item-list">
							<text 
								v-for="(childItem, childIndex) in specChildList" 
								:key="childIndex" class="tit"
								:class="{selected: childItem.selected}"
								@click="selectSpec(childIndex, childItem.pid)"
							>
								{{childItem.name}}
							</text>
						</view>
					</view>
					<view class="number">
						<p>数量</p>
						<yp-number-box :min="0" :max="9" class="peer"></yp-number-box>
					</view>
					<button class="button" @click="toggleSpec">立即购买</button>
				</view>
			</QSPopup>
		</view>
	</view>
</template>

<script>
	import QSPopup from '../../components/QS-popup/QS-popup.vue';
	import ypNumberBox from "@/components/yp-number-box/yp-number-box.vue"
	export default {
		components:{
			QSPopup,
			ypNumberBox
		},
		data () {
			return {
				list:[
					{
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						integral: '积分',
						ptop: '20%'
					}
				],
				details: {
					shop: '商品详情',
					liked: '大家还喜欢'
				},
				//商品详情
				detailsList: [
					{
						name: '碧螺春',
						address: '江苏',
						ptre: '50kg',
						pftre: '罐装'
					}
				],
				//猜你喜欢
				likeList: [
					{
						url: '../../static/shop_pic02.png',
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						recom: '热销推荐'
					},
					{
						url: '../../static/shop_pic02.png',
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						recom: '热销推荐'
					},
					{
						url: '../../static/shop_pic02.png',
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						recom: '热销推荐'
					},
					{
						url: '../../static/shop_pic02.png',
						title: '碧螺春云雾新绿茶罐装明前新茶',
						conent: '中国传统茶艺，中国十大名茶之一，属于绿茶类，已有1000多年历史。',
						price: '50',
						recom: '热销推荐'
					}
				],
				specList: [
					{
						id: 1,
						name: '类型',
					},
				],
				specChildList: [
					{
						id: 1,
						pid: 2,
						name: '碧螺春',
					},
					{
						id: 2,
						pid: 2,
						name: '红茶',
					},
					{
						id: 3,
						pid: 2,
						name: '绿茶',
					},
				]
			}
		},
		onLoad() {
			//规格 默认选中第一条
				// this.specChildList.forEach(item=>{
					// for(let cItem of this.specChildList){
					// 	if(cItem.pid === item.id){
					// 		this.$set(cItem, 'selected', true);
					// 		this.specSelected.push(cItem);
					// 		// break; //forEach不能使用break
					// 	}
					// }
				// })
		},
		methods: {
			//弹出层
			show(ref) {
				this.$refs[ref].show();
			},
			//选择规格
			selectSpec(index, pid){
				let list = this.specChildList;
				list.forEach(item=>{
					if(item.pid === pid){
						this.$set(item, 'selected', false);
					}
				})
				this.$set(list[index], 'selected', true);
				//存储已选择
				this.specSelected = []; 
				list.forEach(item=>{ 
					if(item.selected === true){ 
						this.specSelected.push(item); 
					} 
				})
				
			},
		},
	}


</script>

<style lang="scss" scoped>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 750rpx;
		height: 650rpx;
		background-color: white;
		border-top-left-radius: 10rpx;
		border-top-right-radius: 10rpx;
		position: relative;
	}
	.shop-details {
		width: 100%;
	}
	.shop-details image {
			width: 100%;
			height: 100px;
	}
	.main {
		padding: 22rpx;
	}
	.details-integral {
		font-size: 14px;
	}
	.details-integral text {
			color: #FF0060;
			font-size: 16px;
	}
	.details-integral p {
			margin-top: 10px;
	}
	.details-integral p:nth-of-type(1) {
			color: #FF0060;
			font-size: 17px;
	}
	.details-integral p:nth-of-type(1)	text {
				font-size: 19px;
	}
	.details-integral h5 {
			font-size: 18px;
			margin-top: 5px;
	}
	.details-integral .spn1 {
		display: block;
		width: 40px;
		height: 21px;
		line-height: 21px;
		text-align: center;
		font-size: 10px;
		color: #fff;
		background: #FF0060;
		border-radius: 15px;
		float: left;
	}
	.details-integral .spn2 {
		display: block;
		width: 78px;
		height: 21px;
		line-height: 21px;
		text-align: center;
		float: left;
		font-size: 10px;
		border: 1px solid #FF0060;
		border-radius: 15px;
		margin-left: 15px;
	}
	.div {
		width: 100%;
		height: 30px;
		line-height: 30px;
		margin-top: 10px;
	}
	.details-div {
		margin-top: 15px;
	}
	.details-p {
		height: 30px;
		line-height: 30px;
		border-bottom: 1px solid #ccc;
	}
	.details-p	text {
		display: block;
		height: 20px;
		line-height: 20px;
		font-size: 18px;
		font-weight: 700;
		padding-left: 26rpx;
		border-left: 3px solid #FF0060;
	}
	.details-div-main {
		font-size: 12px;
	}
	.details-div-main	p {
		color: #787878;
		height: 30px;
		line-height: 30px;
		border-bottom: 1px solid #ccc;
		padding-left: 22rpx;
		position: relative;
	}
	.details-div-main	p	text {
		color: #323232;
		position: absolute;
		left: 30%;
	}
	.details-div2 {
		width: 100%;
		height: 1000rpx;
	}
	.details-div2 image {
		width: 100%;
		height: 100%;
	}
	//猜你喜欢
	.details-like {
		padding: 26rpx;
		height: 1000rpx;
	}
	.like-p {
		height: 20px;
		line-height: 20px;
		padding-left: 26rpx;
		border-left: 3px solid #FF0060;
	}
	.details-like-div {
		width: 100%;
		margin-top: 15px;
	}
	.details-like-div view:nth-of-type(odd) {
		float: right;
	}
	.details-like-div view:nth-of-type(even) {
		float: left;
	}
	.liked-shop {
		width: 49%;
		height: 480rpx;
		font-size: 10px;
	}
	.liked-shop image {
		width: 100%;
		height: 110px;
		margin-bottom: 5px;
	}
	.liked-shop p:nth-of-type(1) {
		font-size: 8px;
		margin-top: 5px;
	}
	.liked-shop p:nth-of-type(2) {
		font-size: 12px;
		margin-top: 5px;
		color: #FF0060;
		padding-right: 22rpx;
	}
	.liked-shop p:nth-of-type(2) .spn {
		color: #787878;
		font-size: 8px;
		float: right;
	}
	.price {
		width: 100%;
		height: 100rpx;
		line-height: 100rpx;
		text-align: center;
		color: #fff;
		font-size: 18px;
	}
	.btn {
		background: #FF106A;
	}
	//弹窗
	.a-t{
		display: flex;
		position: absolute;
		top: 0;
		left: 5%;
		padding-bottom: 15rpx;
		border-bottom: 1px solid #ccc;
		image{
			width: 240upx;
			height: 240upx;
			flex-shrink: 0;
			margin-top: -40upx;
			border-radius: 8upx;;
		}
		.right{
			display: flex;
			flex-direction: column;
			padding-left: 24upx;
			font-size: $font-sm + 2upx;
			color: $font-color-base;
			line-height: 42upx;
			.price{
				font-size: $font-lg;
				color: #FF0060;
				margin-bottom: 10upx;
				text-align: left;
				font-size: 18px;
			}
			.selected-text{
				margin-right: 10upx;
			}
		}
	}
	.attr-list{
		display: flex;
		flex-direction: column;
		font-size: $font-base + 2upx;
		color: $font-color-base;
		padding-top: 30upx;
		padding-left: 10upx;
		width: 95%;
		margin-top: 150rpx;
		padding-left: 26rpx;
	}
	.item-list{
		padding: 20upx 0 0;
		display: flex;
		flex-wrap: wrap;
		text{
			display: flex;
			align-items: center;
			justify-content: center;
			background: #eee;
			margin-right: 20upx;
			margin-bottom: 20upx;
			border-radius: 100upx;
			min-width: 60upx;
			height: 60upx;
			padding: 0 20upx;
			font-size: $font-base;
			color: $font-color-dark;
		}
		.selected{
			background: #FF0060;
			color: #fff;
		}
	}
	.number {
		width: 95%;
		padding: 15rpx 26rpx 0 26rpx;
		font-size: 12px;
		height: 100rpx;
		p {
			width: 30%;
			float: left;
			text-align: left;
			padding-left: 22rpx;
		}
	}
	.peer {
		float: right;
		margin-right: 15px;
	}
	.button {
		width: 100%;
		color: #fff;
		background: #FF0060;
		font-size: 14px;
		position: absolute;
		bottom: 0;
	}
</style>
