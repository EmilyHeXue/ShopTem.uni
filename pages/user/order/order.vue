<template>
	<div class="orderList">
		<view class="navBar">
			<view @click="menuClick(index)" v-for="(item,index) in titleList" :key="index" :class="[num == index ? 'navBarlist blueActive' : 'navBarlist']">
				<view class="title">{{item.name}}</view>
			</view>
		</view>
		<view class="orderDetail" v-if="num == 0 || num == 1">
			<view class="topTitle">
				<view class="leftShopName">奶粉店</view>
				<view class="rightStatus">待付款</view>
			</view>
			<view class="orderMessage" @click="toOrderDetail">
				<view class="leftBlock">
					<view class="orderPic"></view>
					<view class="orderName">奶粉 15KG</view>
				</view>
				<view class="rightBlock">
					<view class="topPrice">¥85.8</view>
					<view class="bottomQuantity">x1</view>
				</view>
			</view>
			<view class="orderAllPrice">
				<view class="totalTitle">合计</view>
				<view class="totalPrice">¥109.8</view>
			</view>
			<view class="bottomButton">
				<view class="cancelButton">取消订单</view>
				<view class="continuePay" @click="toConfirmOrder">继续支付</view>
			</view>
		</view>
		<view class="noOrder" v-else>
			<view class="noOrderBlock">
				<view class="title">当前没有订单~</view>
				<view class="button">逛一逛</view>
			</view>
		</view>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				num: 0,
				titleList: [{
					name: '全部'
				}, {
					name: '待付款'
				}, {
					name: '待配送'
				}, {
					name: '待收货'
				}, {
					name: '待评价'
				}]
			}
		},
		onLoad(e) {
			if (e._num == undefined) {
				this.num = 0
			} else {
				this.num = e._num
			}
		},
		methods: {
			toConfirmOrder() {
				uni.navigateTo({
					url:'../../confirmOrder/confirmOrder'
				})
			},
			menuClick(index) {
				this.num = index
			},
			toOrderDetail() {
				uni.navigateTo({
					url:'orderDetail/orderDetail'
				})
			}
		}
	}
</script>

<style lang="scss">
	/*导航加蓝色下划线以及改颜色样式*/
	.blueActive {
		border-bottom: 2px solid #0071ce;
		color: #0071ce;
	}

	.orderList {
		height: 100vh;
		background-color: $uni-bg-color-hover;

		.navBar {
			background-color: #fff;
			padding: 15px 15px 0 15px;
			display: flex;
			color: #676767;
			justify-content: space-between;

			.navBarlist {
				padding-bottom: 15px;
			}
		}

		.orderDetail {
			margin-top: 10px;
			background-color: #fff;
			padding: 10px 0px;

			.topTitle {
				display: flex;
				justify-content: space-between;
				padding: 0 15px;

				.leftShopName {
					font-weight: bold;
					font-size: 17px;
				}

				.rightStatus {
					color: $blue-bgColor;
				}
			}

			.orderMessage {
				display: flex;
				justify-content: space-between;
				padding: 10px;
				margin: 0 15px;
				margin-top: 10px;
				background-color: #f8f8f8;

				.leftBlock {
					display: flex;

					.orderPic {
						width: 80px;
						height: 80px;
						background-color: #fff;
					}

					.orderName {
						margin-left: 10px;
					}
				}

				.rightBlock {
					.topPrice {
						font-weight: bold;
					}

					.bottomQuantity {
						margin-top: 10px;
						color: #5d5d5d;
						text-align: right;
					}
				}
			}

			.orderAllPrice {
				margin-top: 10px;
				padding: 0 15px;
				padding-bottom: 10px;
				border-bottom: 1px solid #ededed;
				display: flex;
				align-items: center;
				justify-content: flex-end;

				.totalTitle {
					margin-right: 8px;
					font-size: 14px;
				}

				.totalPrice {
					color: #ec8132;
					font-weight: bold;
					font-size: 17px;
				}
			}

			.bottomButton {
				margin-top: 10px;
				padding: 0 15px;
				display: flex;
				justify-content: flex-end;

				.cancelButton {
					margin-right: 10px;
					padding: 3px 20px;
					font-size: 15px;
					border-radius: 30px;
					border: 1px solid #cecece;
				}

				.continuePay {
					color: #fff;
					background-color: #ec8131;
					padding: 3px 20px;
					font-size: 15px;
					border-radius: 30px;
				}
			}
		}

		.noOrder {
			text-align: center;

			.noOrderBlock {
				display: inline-block;

				.title {
					margin-top: 150px;
					color: #757575;
				}

				.button {
					margin-top: 30px;
					background-color: #fff;
					border: 1px solid #ec8131;
					border-radius: 30px;
					color: #ec8131;
					font-size: 16px;
					padding: 3px 25px;
				}
			}
		}
	}
</style>
