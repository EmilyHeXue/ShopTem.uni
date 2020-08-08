<template>
	<div class="confirmOrder">
		<view class="topAddress">
			<view class="leftBlock">
				<view class="leftIcon">
					<uni-icon class="rightIcon" type="plus" size="20" color="#adadad"></uni-icon>
				</view>
				<view class="title">请先添加收货地址</view>
			</view>
			<view class="rightIcon">
				<uni-icon class="rightIcon" type="forward" size="20" color="#adadad"></uni-icon>
			</view>
		</view>
		<view class="orderMsg">
			<view class="topTime">
				<view class="leftIcon">
					<uni-icon class="rightIcon" type="forward" size="15" color="#adadad"></uni-icon>
				</view>
				<view class="rightMsg">
					<view class="title">送达时间</view>
					<view class="time">今天17:30</view>
					<view class="rightIcon">
						<uni-icon class="rightIcon" type="forward" size="15" color="#adadad"></uni-icon>
					</view>
				</view>
			</view>
			<view class="orderMsgBlock">
				<view class="leftBlock">
					<view class="orderPic"></view>
					<view class="orderName">可口可乐250g</view>
				</view>
				<view class="rightMsg">
					<view class="topPrice">¥123</view>
					<view class="bottomNum">x1</view>
				</view>
			</view>
			<view class="buyerLeaveMsg">
				<view class="leftTitle">买家留言</view>
				<view class="rightInput">
					<input placeholder-class="phcolor" class="input" placeholder="填写给卖家的留言" />
				</view>
			</view>
		</view>
		<view class="invoice">
			<view class="leftTitle">发票</view>
			<view class="rightBlock">
				<view class="invoiceMsg">个人(普通电子发票)</view>
				<view class="rightIcon">
					<uni-icon class="rightIcon" type="forward" size="15" color="#adadad"></uni-icon>
				</view>
			</view>
		</view>
		<view class="orderPriceBlock">
			<view class="orderPrice">
				<view class="leftTitle">商品金额</view>
				<view class="rightPrice">¥123</view>
			</view>
			<view class="shopFee">
				<view class="leftTitle">配送费</view>
				<view class="rightPrice">
					<view class="plus">+</view>
					<view class="price">¥123</view>
				</view>
			</view>
			<view class="packageFee">
				<view class="leftTitle">包装费</view>
				<view class="rightPrice">
					<view class="plus">+</view>
					<view class="price">¥123</view>
				</view>
			</view>
			<view class="actuallyPay">
				<view class="leftTitle">实际支付</view>
				<view class="rightPrice">¥123</view>
			</view>
		</view>
		<view class="bottomConfirm">
			<view class="title">合计</view>
			<view class="price">¥123</view>
			<view class="confirmButton">提交订单</view>
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
	.phcolor {
		/*placeholder颜色*/
		color: #cecece;
	}

	.topAddress {
		display: flex;
		padding: 25rpx 30rpx;
		align-items: center;
		justify-content: space-between;
		border-bottom: 10px solid #f8f8f8;

		.leftBlock {
			display: flex;
			align-items: center;

			.title {
				margin-left: 20rpx;
				font-size: 19px;
				color: #0071ce;
				font-weight: bold;
			}
		}
	}

	.orderMsg {
		padding: 0 30rpx;
		border-bottom: 10px solid #f8f8f8;

		.topTime {
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 30rpx 0;

			.rightMsg {
				display: flex;
				align-items: center;

				.title {
					color: #9b9b9b;
					margin-right: 20rpx;
				}

				.time {
					color: #0071ce;
					font-size: 19px;
					margin-right: 20rpx;
				}
			}
		}

		.orderMsgBlock {
			background-color: #f8f8f8;
			padding: 10px;
			margin-bottom: 10px;
			display: flex;
			justify-content: space-between;

			.leftBlock {
				display: flex;

				.orderPic {
					width: 80px;
					height: 80px;
					background-color: #fff;
				}

				.orderName {
					margin-left: 20rpx;
				}
			}

			.rightMsg {
				text-align: right;
				color: #5d5d5d;
				font-weight: bold;

				.bottomNum {
					margin-top: 10rpx;
				}
			}
		}

		.buyerLeaveMsg {
			display: flex;
			align-items: center;
			padding: 40rpx 0;
			border-top: 1px solid #dadada;

			.rightInput {
				margin-left: 40rpx;
			}
		}
	}

	.invoice {
		padding: 40rpx 30rpx;
		display: flex;
		justify-content: space-between;
		border-bottom: 10px solid #f8f8f8;

		.rightBlock {
			display: flex;

			.invoiceMsg {
				margin-left: 20rpx;
			}
		}
	}

	.orderPriceBlock {
		border-bottom: 73px solid #f8f8f8;
		padding: 0 30rpx;

		.orderPrice {
			display: flex;
			justify-content: space-between;
			padding: 30rpx 0 15rpx 0;

			.leftTitle {
				color: #c7c7c7;
			}

			.rightPrice {
				display: flex;
				color: #5d5d5d;
			}
		}

		.shopFee {
			display: flex;
			justify-content: space-between;
			padding: 15rpx 0 15rpx 0;

			.leftTitle {
				color: #c7c7c7;
			}

			.rightPrice {
				display: flex;
				color: #5d5d5d;

				.plus {
					margin-right: 10rpx;
				}
			}
		}

		.packageFee {
			display: flex;
			justify-content: space-between;
			padding: 15rpx 0 30rpx 0;
			border-bottom: 1px solid #e9e9e9;

			.leftTitle {
				color: #c7c7c7;
			}

			.rightPrice {
				display: flex;
				color: #5d5d5d;

				.plus {
					margin-right: 10rpx;
				}
			}
		}

		.actuallyPay {
			display: flex;
			justify-content: space-between;
			padding: 15rpx 0 30rpx 0;

			.leftTitle {
				color: #c7c7c7;
			}

			.rightPrice {
				display: flex;
				color: #ec8131;
				font-weight: bold;
			}
		}
	}

	.bottomConfirm {
		position: fixed;
		bottom: 0;
		width: 100%;
		padding: 20rpx 30rpx;
		display: flex;
		align-items: center;
		justify-content: flex-end;
		box-sizing: border-box;
		background-color: #fff;
		box-shadow: 0 0 10px #ededed;

		.title {
			margin-right: 20rpx;
		}

		.price {
			margin-right: 20rpx;
			color: #ec8131;
			font-size: 20px;
			font-weight: bold;
		}

		.confirmButton {
			background-color: #cecece;
			color: #fff;
			padding: 15rpx 40rpx;
			border-radius: 20px;
		}
	}
</style>
