<template>
	<view class="user">
		<view class="topMsgBox">
			<image @click="toUserMsg" class="topMsgBox-img" :src="yonghuwx.avatarUrl"></image>
			<view class="topMsgBox-name">{{yonghuwx.nickName}}</view>
		</view>
		<view class="content">
			<view class="order">
				<view class="order-topBanner">
					<view class="order-topBanner-left">
						<view class="order-topBanner-left-leftTitle">全部订单</view>
					</view>
					<view class="order-topBanner-right" @click="toAllOrder">
						<view class="order-topBanner-right-rightTitle">查看全部订单</view>
						<uni-icon class="order-topBanner-right-rightIcon" type="forward" size="20" color="#999"></uni-icon>
					</view>
				</view>
				<view class="order-orderList">
					<navigator url="/pages/user/order/order?_num=1" class="order-orderList-pendingPay">
						<uni-icon class="order-orderList-pendingPay-topIcon" type="person" size="30" color="#000"></uni-icon>
						<view class="order-orderList-pendingPay-title">待付款</view>
					</navigator>
					<navigator url="/pages/user/order/order?_num=2" class="order-orderList-pendingDelever">
						<uni-icon class="order-orderList-pendingDelever-topIcon" type="person" size="30" color="#000"></uni-icon>
						<view class="order-orderList-pendingDelever-title">待配送</view>
					</navigator>
					<navigator url="/pages/user/order/order?_num=3" class="order-orderList-pendingReceipt">
						<uni-icon class="order-orderList-pendingReceipt-topIcon" type="person" size="30" color="#000"></uni-icon>
						<view class="order-orderList-pendingReceipt-title">待收货</view>
					</navigator>
					<navigator url="/pages/user/order/order?_num=4" class="order-orderList-pendingComment">
						<uni-icon class="order-orderList-pendingComment-topIcon" type="person" size="30" color="#000"></uni-icon>
						<view class="order-orderList-pendingComment-title">待评价</view>
					</navigator>
				</view>
			</view>
			<view class="research">
				<view class="research-block">
					<view class="research-block-left">今天我们做的怎么样</view>
					<view class="research-block-right">
						<view class="research-block-right-topTitle">点击进入</view>
						<view class="order-research-block-right-bottomTitle">参与调研</view>
					</view>
				</view>
			</view>
			<view class="contentList">
				<view class="contentList-top">
					<view class="contentList-top-receiptAddress" @click="toCoupon">
						<view class="contentList-top-receiptAddress-left">优惠券</view>
						<view class="contentList-top-receiptAddress-right">
							<uni-icon class="contentList-top-receiptAddress-right-rightIcon" type="forward" size="20" color="#999"></uni-icon>
						</view>
					</view>
					<view class="contentList-top-coupon" @click="toAddress">
						<view class="contentList-top-coupon-left">收货地址</view>
						<view class="contentList-top-coupon-right">
							<uni-icon class="contentList-top-coupon-right-rightIcon" type="forward" size="20" color="#999"></uni-icon>
						</view>
					</view>
					<view class="contentList-top-afterSale" @click="toSale">
						<view class="contentList-top-afterSale-left">售后</view>
						<view class="contentList-top-afterSale-right">
							<uni-icon class="contentList-top-afterSale-right-rightIcon" type="forward" size="20" color="#999"></uni-icon>
						</view>
					</view>
				</view>
				<view class="contentList-bottom">
					<view class="contentList-bottom-scanCodeBuy">
						<view class="contentList-bottom-scanCodeBuy-left">扫码购</view>
						<view class="contentList-bottom-scanCodeBuy-right">
							<uni-icon class="contentList-bottom-scanCodeBuy-right-rightIcon" type="forward" size="20" color="#999"></uni-icon>
						</view>
					</view>
					<button class="contentList-bottom-contactService" open-type="contact">
						<view class="contentList-bottom-contactService-left">联系客服</view>
						<view class="contentList-bottom-contactService-right">
							<uni-icon class="contentList-bottom-contactService-right-rightIcon" type="forward" size="20" color="#999"></uni-icon>
						</view>
					</button>
					<view class="contentList-bottom-disclaimer">
						<view class="contentList-bottom-disclaimer-left">免责声明</view>
						<view class="contentList-bottom-disclaimer-right">
							<uni-icon class="contentList-bottom-disclaimer-right-rightIcon" type="forward" size="20" color="#999"></uni-icon>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {
				yonghuwx: []
			}
		},
		components: {
			uniIcon
		},
		methods: {
			toAddress() {//收货地址
				uni.navigateTo({
					url:"address/address"
				})
			},
			toCoupon() {//优惠券
				uni.navigateTo({
					url:"coupon/coupon"
				})
			},
			toUserMsg() {//用户中心
				uni.navigateTo({
					url:"userMsg/userMsg"
				})
			},
			toSale() {//售后
				uni.navigateTo({
					url:"afterSale/afterSale"
				})
			},
			toAllOrder() {//全部订单
				uni.navigateTo({
					url:"order/order"
				})
			}
		},
		onLoad() {
			let that = this;
			uni.login({
				provider: 'weixin',
				success: function(loginRes) {
					// 获取用户信息				
					uni.getUserInfo({
						provider: 'weixin',
						success: function(infoRes) {
							that.yonghuwx = infoRes.userInfo
						}
					});
				}
			});
		}
	}
</script>

<style lang="scss">
	.user {
		height: 100%;
		background-color: $uni-bg-color-grey;

		.topMsgBox {
			padding: 25px 0 35px 0;
			background-color: $blue-bgColor;
			display: flex;
			flex-direction: column;
			align-items: center;

			&-img {
				width: 128rpx;
				height: 128rpx;
				margin: 20rpx;
				border-radius: 50%;
			}

			&-name {
				color: #fff;
			}
		}

		.content {
			background-color: #f8f8f8;
			padding-bottom: 10px;

			.order {
				padding: 10px 0 0 0;
				font-size: 15px;

				&-topBanner {
					display: flex;
					background-color: #fff;
					padding: 15px;
					border-bottom: 1px solid #ededed;
					align-items: center;
					justify-content: space-between;

					&-left {
						font-weight: bold;
					}

					&-right {
						display: flex;
						align-items: center;

						&-rightTitle {
							margin-right: 5px;
							color: #999;
						}
					}
				}

				&-orderList {
					background-color: #fff;
					display: flex;
					padding: 20px 0;
					font-size: 15px;
					color: #666;
					justify-content: space-around;
					text-align: center;
				}
			}

			.research {
				padding: 10px 12px;

				&-block {
					background-color: #0071ce;
					border-radius: 10px;
					padding: 12px 15px;
					display: flex;
					color: #fff;
					align-items: center;
					justify-content: space-between;

					&-left {
						padding-right: 15px;
						font-size: 13px;
						border-right: 1px solid #fff;
					}

					&-right {
						background-color: #fff;
						color: #0071ce;
						padding: 5px 12px;
						font-size: 13px;
						border-radius: 5px;
					}
				}
			}

			.contentList {
				&-top {
					background-color: #fff;

					&-coupon,
					&-receiptAddress,
					&-afterSale {
						display: flex;
						align-items: center;
						justify-content: space-between;
						padding: 15px;
						font-size: 14px;
						font-weight: bold;
						border-bottom: 1px solid #ededed;
					}
				}

				&-bottom {
					margin-top: 10px;
					background-color: #fff;

					&-scanCodeBuy,
					&-contactService,
					&-disclaimer {
						display: flex;
						align-items: center;
						justify-content: space-between;
						padding: 15px;
						font-size: 14px;
						font-weight: bold;
					}

					&-contactService {
						padding: 0 15px;
						background-color: #fff;

						&-right {
							display: flex;
							align-items: center;
						}
					}

					&-disclaimer {
						border-bottom: 0;
					}
				}
			}
		}
	}
</style>
