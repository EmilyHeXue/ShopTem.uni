<template>
	<div class="shopDetail">
		<swiper style="height: 700rpx;" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<div v-for="(item,index) in background" :key="index">
				<swiper-item>
					<image :src="item.url" class="slide-image" mode="aspectFill"></image>
				</swiper-item>
			</div>
		</swiper>
		<view class="orderMsgBlock">
			<view class="orderMsg">
				<view class="leftBlock">
					<uni-icon class="rightIcon" type="trash" size="20" color="#adadad"></uni-icon>
					<view class="title">沃尼玛 维他柠檬茶 爽过吸大麻</view>
				</view>
				<view class="rightShare">
					<uni-icon class="rightIcon" type="upload" size="20" color="#adadad"></uni-icon>
				</view>
			</view>
			<view class="orderPrice">
				<view class="sign">¥</view>
				<view class="price">123</view>
			</view>
			<view class="orderTime">
				<uni-icon class="rightIcon" type="trash" size="25" color="#adadad"></uni-icon>
				<view class="title">最快90分钟送达</view>
			</view>
		</view>
		<view class="couponBlock">
			<view class="getCoupon">
				<view class="title">领券</view>
				<uni-icon class="rightIcon" type="forward" size="20" color="#adadad"></uni-icon>
			</view>
			<view class="promote">
				<view class="title">促销</view>
				<uni-icon class="rightIcon" type="forward" size="20" color="#adadad"></uni-icon>
			</view>
		</view>
		<view class="chooseMuchBlock">
			<view class="leftBlock">
				<view class="title">已选择</view>
				<view class="quantity">1件</view>
			</view>
			<uni-icon class="rightIcon" type="forward" size="20" color="#adadad"></uni-icon>
		</view>
		<view class="orderDetailBlock">
			<view class="leftLine"></view>
			<view class="centerTitle">商品详情</view>
			<view class="rightLine"></view>
		</view>
		<view class="orderDetailPic">
			<view class="title">商品暂无详情</view>
		</view>
		<view class="bottomBlock">
			<view class="leftIcon">
				<view class="home">
					<uni-icon class="homeIcon" type="forward" size="10" color="#adadad"></uni-icon>
					<view class="title">首页</view>
				</view>
				<view class="shopCart">
					<uni-icon class="homeIcon" type="forward" size="10" color="#adadad"></uni-icon>
					<view class="title">购物车</view>
				</view>
			</view>
			<view class="rightButton">加入购物车</view>
		</view>
	</div>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {
				background: [{
						url: '../../static/微信图片_20191107095401.jpg',
					},
					{
						url: '../../static/微信图片_20191107100644.jpg',
					},
					{
						url: '../../static/微信图片_20191107100656.jpg',
					},
				],
			}
		},
		components: {
			uniIcon
		}
	}
</script>

<style lang="scss">
	/* 轮播图 */
	.slide-image {
		width: 100%;
		height: 100%;
	}

	.orderMsgBlock {
		padding: 0rpx 30rpx;
		border-bottom: 10px solid #f8f8f8;

		.orderMsg {
			display: flex;
			padding: 30rpx 0;
			justify-content: space-between;

			.leftBlock {
				display: flex;

				.title {
					font-size: 20px;
					font-weight: bold;
					margin-left: 20rpx;
				}
			}
		}

		.orderPrice {
			display: flex;
			align-items: center;
			padding: 0 10rpx;
			border-bottom: 1px solid #eee;
			color: #ec8131;

			.price {
				margin-left: 15rpx;
				font-size: 25px;
				font-weight: bold;
			}
		}

		.orderTime {
			padding: 30rpx 0;
			display: flex;
			align-items: center;

			.title {
				margin-left: 10rpx;
				color: #757575;
				font-weight: bold;
			}
		}
	}

	.couponBlock {
		border-bottom: 10px solid #f8f8f8;

		.getCoupon {
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 30rpx;
			border-bottom: 1px solid #eee;
		}

		.promote {
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 30rpx;
		}
	}

	.chooseMuchBlock {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 30rpx;

		.leftBlock {
			display: flex;
			align-items: center;
			color: #282828;

			.quantity {
				margin-left: 20rpx;
			}
		}
	}

	.orderDetailBlock {
		background-color: #f8f8f8;
		padding: 40rpx 30rpx;
		display: flex;
		align-items: center;

		.leftLine {
			height: 1px;
			background-color: #e0e0e0;
			width: 35%;
		}

		.centerTitle {
			width: 33%;
			font-size: 17px;
			text-align: center;
			padding-left: 7rpx;
		}

		.rightLine {
			height: 1px;
			width: 33%;
			background-color: #e0e0e0;
		}
	}

	.orderDetailPic {
		padding-bottom: 67px;
	}

	.bottomBlock {
		position: fixed;
		bottom: 0;
		width: 100%;
		background-color: #fff;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 10rpx 30rpx;
		box-sizing: border-box;
		border-top: 1px solid #eee;

		.leftIcon {
			display: flex;
			text-align: center;
			font-size: 15px;
			color: #adadad;

			.shopCart {
				margin-left: 40rpx;
			}
		}

		.rightButton {
			width: 60%;
			background-color: #ec8131;
			color: #fff;
			text-align: center;
			padding: 20rpx 0;
			border-radius: 30px;
		}
	}
</style>
