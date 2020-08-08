<template>
	<div class="orderDetail">
		<view class="topBlock">
			<view class="leftBlock">
				<view class="topTitle">已取消</view>
				<view class="bottomTitle">订单未付款，超时自动关闭</view>
			</view>
			<view class="rightBlock">
				<uni-icon class="topIcon" type="close" size="20" color="#fff"></uni-icon>
			</view>
		</view>
		<view class="receiveMsg">
			<view class="topMsg">
				<view class="left">
					<uni-icon class="topIcon" type="location" size="20" color="#232323"></uni-icon>
					<view class="receiver">收货人：张某某</view>
				</view>
				<view class="right">
					<view class="phone">123456789</view>
				</view>
			</view>
			<view class="bottomAddress">
				<view class="addressMsg">广东省深圳市福田区富民路广东省深圳市福田区富民路广东省深圳市福田区富民路</view>
			</view>
		</view>
		<view class="orderMsgBlock">
			<view class="top">
				<view class="left">
					<uni-icon class="leftIcon" type="close" size="20" color="#232323"></uni-icon>
					<view class="shopName">沃尼玛-华强北店</view>
				</view>
				<view class="right">
					<uni-icon class="rightIcon" type="close" size="20" color="#fff"></uni-icon>
					<view class="rightTitle">联系客服</view>
				</view>
			</view>
			<view class="orderMsg">
				<view class="leftMsg">
					<view class="orderImg"></view>
					<view class="orderName">酸角糕 160g</view>
				</view>
				<view class="rightPrice">
					<view class="topPrice">￥9.9</view>
					<view class="bottomAmount">x1</view>
				</view>
			</view>
			<view class="buyerMsg">
				<view class="leftBuyerMsgTitle">买家留言</view>
				<view class="rightBuyerMsg">其他商品继续配送</view>
			</view>
		</view>
		<view class="priceBlock">
			<view class="orderPrice">
				<view class="title">商品金额</view>
				<view class="rightPrice">￥9.9</view>
			</view>
			<view class="deliveryFees">
				<view class="title">配送费</view>
				<view class="rightFees">+￥6</view>
			</view>
			<view class="actualPay">
				<view class="title">实际支付</view>
				<view class="rightPay">￥15.9</view>
			</view>
		</view>
		<view class="orderTime">
			<view class="orderNo">
				<view class="title">订单编号</view>
				<view class="rightNo">
					<view class="number">123456789</view>
					<view class="copyButton">复制</view>
				</view>
			</view>
			<view class="payTime">
				<view class="title">下单时间</view>
				<view class="rightTime">2019.10.30 11:23:27</view>
			</view>
			<view class="cancelPay">
				<view class="title">取消时间</view>
				<view class="rightTime">2019.10.30 11:53:27</view>
			</view>
		</view>
		<view class="greyBlock"></view>
		<view class="bottomBlock">
			<view class="bottomButton">删除订单</view>
		</view>
	</div>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		components: {
			uniIcon
		}
	}
</script>

<style lang="scss">
	.topBlock {
		background-color: #0071ce;
		color: #fff;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 40rpx 60rpx;

		.leftBlock {
			.topTitle {
				font-size: 25px;
				font-weight: bold;
			}
		}
	}

	.receiveMsg {
		padding: 15px;
		border-bottom: 10px solid #f8f8f8;

		.topMsg {
			display: flex;
			justify-content: space-between;
			font-weight: bold;

			.left {
				display: flex;
				align-items: center;

				.receiver {
					margin-left: 10rpx;
				}
			}
		}

		.bottomAddress {
			margin-top: 10rpx;
			padding-left: 60rpx;

			.addressMsg {
				font-size: 16px;
				color: #666;
			}
		}
	}

	.orderMsgBlock {
		border-bottom: 10px solid #f8f8f8;

		.top {
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 10px 15px;
			border-bottom: 1px solid #ededed;

			.left {
				display: flex;
				align-items: center;

				.shopName {
					margin-left: 10rpx;
					margin-top: 8rpx;
					font-size: 38rpx;
					font-weight: bold;
				}
			}

			.right {
				display: flex;
				color: #0071ce;

				.rightTitle {
					margin-top: 2px;
					margin-left: 10rpx;
				}
			}
		}

		.orderMsg {
			margin: 10px 15px 0 15px;
			background-color: #f8f8f8;
			display: flex;
			justify-content: space-between;
			padding: 10px;

			.leftMsg {
				display: flex;
				align-items: flex-start;

				.orderName {
					margin-left: 20rpx;
					color: #555;
				}

				.orderImg {
					width: 125rpx;
					height: 125rpx;
					background-color: #0071ce;
				}
			}

			.rightPrice {
				color: #5d5d5d;
				font-weight: bold;

				.bottomAmount {
					text-align: right;
					margin-top: 3px;
				}
			}
		}

		.buyerMsg {
			margin-top: 45rpx;
			margin-left: 15px;
			margin-bottom: 35rpx;
			display: flex;
			align-items: center;

			.leftBuyerMsgTitle {
				font-size: 18px;
				color: #5d5d5d;
				font-weight: bold;
			}

			.rightBuyerMsg {
				margin-left: 80rpx;
			}
		}
	}

	.priceBlock {
		padding: 20px 15px 10px 15px;
		font-size: 15px;
		color: #4a4a4a;
		border-bottom: 10px solid #f8f8f8;

		.orderPrice {
			display: flex;
			justify-content: space-between;
		}

		.deliveryFees {
			display: flex;
			justify-content: space-between;
			margin-top: 10rpx;
			padding-bottom: 10px;
			border-bottom: 1px solid #ededed;
		}

		.actualPay {
			display: flex;
			justify-content: space-between;
			margin-top: 10px;

			.rightPay {
				color: #f1a064;
			}
		}
	}

	.orderTime {
		padding: 20px 15px;
		font-size: 15px;
		color: #a5a5a5;

		.orderNo {
			display: flex;
			justify-content: space-between;

			.number {
				margin-right: 30rpx;
			}

			.rightNo {
				display: flex;

				.number {
					font-weight: bold;
				}

				.copyButton {
					color: #6a6a6a;
				}
			}
		}

		.payTime {
			display: flex;
			justify-content: space-between;
			margin-top: 10rpx;

			.rightTime {
				font-weight: bold;
			}
		}

		.cancelPay {
			display: flex;
			justify-content: space-between;
			margin-top: 10rpx;

			.rightTime {
				font-weight: bold;
			}
		}
	}

	.greyBlock {
		height: 20rpx;
		background-color: #f8f8f8;
		padding-bottom: 134rpx;
	}

	.bottomBlock {
		position: fixed;
		bottom: 0;
		width: 100%;
		padding: 15px;
		background-color: #fff;
		display: flex;
		justify-content: flex-end;
		box-sizing: border-box;

		.bottomButton {
			border: 1px solid #d6d6d6;
			padding: 5px 20px;
			border-radius: 40px;
		}
	}
</style>
