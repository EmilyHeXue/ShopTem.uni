<template>
	<div class="shopCart">
		<view class="greyBlock"></view>
		<view class="shopBlock">
			<view class="topShopBlock">
				<view class="left">
					<uni-icon class="rightIcon" type="checkbox-filled" size="20" color="#adadad"></uni-icon>
					<view class="shopMessage">
						<view class="topTitle">沃尼玛-华强北店</view>
						<view class="bottomMsg">已选择一件</view>
					</view>
				</view>
				<view class="right">优惠券</view>
			</view>
			<view class="orderBlock">
				<view class="leftBlock">
					<uni-icon class="rightIcon" type="checkbox-filled" size="20" color="#adadad"></uni-icon>
					<view class="orderImg" @click="toShopDetail"></view>
				</view>
				<view class="rightMsg">
					<view class="topMsg">劲爆 新一代芦荟</view>
					<view class="bottomPrice">
						<view class="leftPrice">¥123</view>
						<view class="rightStep">
							<view class="minus">一</view>
							<view class="number">1</view>
							<view class="plus">
								<uni-icon class="rightIcon" type="plusempty" size="20" color="#adadad"></uni-icon>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="bottomFixBlock">
			<view class="leftBlock">
				<uni-icon class="rightIcon" type="checkbox-filled" size="20" color="#adadad"></uni-icon>
				<view class="chooseAll">全选</view>
				<view class="delete">删除</view>
			</view>
			<view class="rightMsg">
				<view class="leftPrice">
					<view class="title">合计</view>
					<view class="price">¥12345</view>
				</view>
				<view class="rightButton" @click="toConfirmOrder">去结算</view>
			</view>
		</view>
		<view class="guessYouLike">
			<view class="leftLine"></view>
			<view class="centerTitle">猜你喜欢</view>
			<view class="rightLine"></view>
		</view>
		<view class="guessOrderList">
			<view class="orderMsg" @click="toShopDetail" v-for="(item,index) in guessOrderList" :key="index">
				<view class="topPic"></view>
				<view class="orderName">{{item.name}}</view>
				<view class="conditionBlock">
					<view class='condition'>{{item.condition}}</view>
					<view class="coupon">{{item.coupon}}</view>
				</view>
				<view class="priceBlock">
					<view class="leftPrice">¥{{item.price}}</view>
					<view class="rightAddToCartButton">
						<uni-icon class="rightIcon" type="checkbox-filled" size="20" color="#adadad"></uni-icon>
					</view>
				</view>
			</view>
		</view>
	</div>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {
				guessOrderList: [{
						id: 1,
						name: '百事可乐',
						price: '2',
						coupon: "满100减101",
						condition: '限购3件'
					},
					{
						id: 2,
						name: '维他柠檬茶',
						price: '345',
						coupon: "满999减101",
						condition: '限购3件'
					},
					{
						id: 3,
						name: '金龙鱼',
						price: '568',
						coupon: "满999减101",
						condition: '限购3件'
					},
					{
						id: 4,
						name: '金龙鱼',
						price: '568',
						coupon: "满999减101",
						condition: '限购3件'
					},
				]
			}
		},
		methods: {
			toShopDetail() {
				uni.navigateTo({
					url:'../shopDetail/shopDetail'
				})
			},
			toConfirmOrder() {
				uni.navigateTo({
					url:'../confirmOrder/confirmOrder'
				})
			}
		},
		components: {
			uniIcon
		}
	}
</script>

<style lang="scss">
	.shopCart {
		background-color: #f2f2f2;

		.greyBlock {
			height: 10px;
			background-color: #f2f2f2;
		}

		.shopBlock {
			background-color: #fff;
			margin: 0 20rpx;
			border-radius: 5px;
			box-shadow: 0 0 10px #ebebeb;

			.topShopBlock {
				display: flex;
				padding: 30rpx;
				justify-content: space-between;

				.left {
					display: flex;

					.shopMessage {
						margin-left: 20rpx;

						.topTitle {
							font-size: 18px;
							color: #000;
							font-weight: bold;
						}

						.bottomMsg {
							color: #adadad;
							font-size: 15px;
						}
					}
				}

				.right {
					color: #ec8131;
				}
			}

			.orderBlock {
				background-color: #fef8f3;
				display: flex;
				padding: 30rpx;

				.leftBlock {
					display: flex;
					align-items: center;

					.orderImg {
						height: 80px;
						width: 80px;
						background-color: #fff;
						margin-left: 10px;
					}
				}

				.rightMsg {
					margin-left: 20rpx;
					width: 100%;

					.bottomPrice {
						display: flex;
						align-items: center;
						justify-content: space-between;
						padding-top: 70rpx;

						.leftPrice {
							color: #ec8131;
							font-size: 17px;
							font-weight: bold;
						}

						.rightStep {
							display: flex;
							color: #adadad;
							border: 1px solid #adadad;

							.minus {
								padding: 5rpx 10rpx;
							}

							.number {
								border-left: 1px solid #adadad;
								color: #000;
								font-weight: bold;
								border-right: 1px solid #adadad;
								padding: 5rpx 10rpx;
							}

							.plus {
								padding: 5rpx 10rpx;
							}
						}
					}
				}
			}
		}

		.guessYouLike {
			margin: 40rpx 20rpx;
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

		.guessOrderList {
			padding-bottom: 113px;
			margin: 0 20rpx;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;

			.orderMsg {
				background-color: #fff;
				width: 43%;
				padding: 10px;
				margin-bottom: 18rpx;
				border-radius: 5px;

				.topPic {
					width: 100%;
					height: 300rpx;
					background-color: #0071ce;
				}

				.orderName {
					margin-top: 10rpx;
				}

				.conditionBlock {
					margin-top: 20rpx;

					.condition {
						font-size: 15px;
						color: #adadad;
					}

					.coupon {
						font-size: 10px;
						color: #ec8131;
						background-color: #fef2e8;
						display: inline-block;
						padding: 4rpx 8rpx;
						border-radius: 40rpx;
						border: 1px solid #ec8131;
					}
				}

				.priceBlock {
					display: flex;
					align-items: center;
					justify-content: space-between;
					margin-top: 40rpx;

					.leftPrice {
						color: #ec8131;
						font-size: 20px;
						font-weight: bold;
					}
				}
			}
		}

		.bottomFixBlock {
			position: fixed;
			bottom: 0px;
			width: 100%;
			display: flex;
			align-items: center;
			justify-content: space-between;
			background-color: #fff;
			padding: 10px;
			box-sizing: border-box;
			box-shadow: 0 0 5px #ebebeb;
			z-index: 999;

			.leftBlock {
				display: flex;
				align-items: center;

				.chooseAll {
					margin-left: 10rpx;
					color: #adadad;
				}

				.delete {
					margin-left: 20rpx;
					color: #0071ce;
				}
			}

			.rightMsg {
				display: flex;
				align-items: center;

				.leftPrice {
					display: flex;
					align-items: center;
					margin-right: 20rpx;

					.title {
						color: #adadad;
						margin-right: 10rpx;
					}

					.price {
						color: #ec8131;
						font-weight: bold;
					}
				}

				.rightButton {
					padding: 5px 18px;
					background-color: #0071ce;
					color: #fff;
					border-radius: 30px;
				}
			}
		}
	}
</style>
