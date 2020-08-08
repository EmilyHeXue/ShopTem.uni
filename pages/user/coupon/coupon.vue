<template>
	<div class="coupon">
		<div class="navBar">
			<view @click="menuClick(index)" v-for="(item,index) in titleList" :key="index" :class="[num == index ? 'navBarlist blueActive' : 'navBarlist']">
				<view class="title">{{item.name}}</view>
			</view>
		</div>
		<view class="couponList" v-if="num==0">
			<view class="topBlock">
				<view class="leftBlock">
					<view class="left">
						<view class="price">
							<view class="icon">¥</view>
							<view class="number">15</view>
						</view>
						<view class="condition">满129可用</view>
					</view>
					<view class="center">
						<view class="top">【全场券】127减10</view>
						<view class="time">2019.10.31 00:00-2019.10.31 23:59</view>
						<view class="condition">部分商品可用</view>
					</view>
				</view>
				<view class="rightBlock">
					<view class="remind">今天过期</view>
					<view class="bottomButton">去使用</view>
				</view>
			</view>
			<view class="bottomBlock">
				<view class="left">部分线上门店适用</view>
				<view class="right">
					<view class="title">规则详情</view>
					<uni-icon class="rightIcon" type="forward" size="20" color="#999"></uni-icon>
				</view>
			</view>
		</view>
		<view class="noCoupon" v-if="num==1">
			<view class="title">还没有优惠券噢</view>
			<view class="button" @click="toGetCoupon">去领券</view>
		</view>
		<view class="expired couponList" v-if="num==2">
			<view class="topBlock">
				<view class="leftBlock">
					<view class="left">
						<view class="price">
							<view class="icon">¥</view>
							<view class="number">15</view>
						</view>
						<view class="condition">满129可用</view>
					</view>
					<view class="center">
						<view class="top">【全场券】129减10</view>
						<view class="time">2019.10.31 00:00-2019.10.31 23:59</view>
					</view>
				</view>
			</view>
		</view>
		<view class="bottom" @click="toGetCoupon">去领券中心</view>
	</div>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {
				num: 0,
				titleList: [{
					name: '可使用'
				}, {
					name: '已使用'
				}, {
					name: '已过期'
				}]
			}
		},
		components: {
			uniIcon
		},
		methods: {
			menuClick(index) {
				this.num = index
			},
			toGetCoupon() {
				uni.navigateTo({
					url:"couponList/couponList"
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

	.coupon {
		background-color: #f8f8f8;
		height: 100vh;

		.navBar {
			background-color: #fff;
			padding: 15px 15px 0 15px;
			display: flex;
			color: #676767;
			font-weight: bold;
			justify-content: space-around;

			.navBarlist {
				padding-bottom: 15px;
			}
		}

		.couponList {
			margin: 10px 15px 0 15px;
			background-color: #fff;
			border-radius: 10px;
			font-size: 15px;
			padding: 15px 12px 8px 15px;
			box-shadow: 0 0 15px #ebebeb;
			border-top: 3px solid #62b34c;
			position: relative;
			overflow: hidden;

			.topBlock {
				display: flex;
				align-items: center;
				justify-content: space-between;
				border-bottom: 1px dashed #ebebeb;
				padding-bottom: 20px;

				::before {
					width: 13px;
					height: 13px;
					content: '';
					position: absolute;
					left: -7px;
					bottom: 46px;
					background-color: #ececec;
					border-radius: 50%;
				}

				::after {
					width: 13px;
					height: 13px;
					content: '';
					position: absolute;
					right: -7px;
					bottom: 46px;
					background-color: #ececec;
					border-radius: 50%;
				}

				.leftBlock {
					color: #ec8131;
					display: flex;
					align-items: flex-start;

					.price {
						display: flex;
						align-items: baseline;
						justify-content: space-around;
						font-weight: bold;
						margin-top: 5px;

						.number {
							font-size: 30px;
						}
					}

					.condition {
						font-size: 22rpx;
						margin-top: -5px;
					}
				}

				.center {
					margin-top: 5px;
					margin-left: 25rpx;

					.top {
						font-size: 17px;
						color: #000;
						font-weight: bold;
					}

					.time {
						font-size: 22rpx;
						color: #9b9b9b;
					}

					.condition {
						color: #9b9b9b;
						margin-top: 0;
					}
				}

				.rightBlock {
					.remind {
						color: #ec8131;
						font-size: 22rpx;
						text-align: center;
					}

					.bottomButton {
						text-align: center;
						color: #fff;
						background-color: #0071ce;
						padding: 10rpx 20rpx;
						font-size: 28rpx;
						margin-top: 3px;
						border-radius: 30px;
					}
				}
			}
			.bottomBlock {
				padding-top: 10px;
				display: flex;
				align-items: center;
				justify-content: space-between;
				color: #8c8c8c;
				
			
				.right {
					display: flex;
					align-items: center;
			
					.rightIcon {
						margin-top: 3px;
					}
				}
			}
		}

		.expired {
			border-top: 3px solid #9b9b9b;

			.leftBlock {
				color: #9b9b9b !important;
				align-items: center !important;

				.center {
					margin-top: 0px;
					margin-left: 20px !important;

					.top {
						color: #9b9b9b !important;
						margin-top: 15px;
					}

					.time {
						margin-top: 10px;
					}
				}
			}

			.topBlock {
				border-bottom: 0;

				::before {
					width: 0px;
					height: 0px;
				}

				::after {
					width: 0px;
					height: 0px;
				}
			}
		}

		.noCoupon {
			margin: auto;
			margin-top: 200rpx;
			width: 300rpx;

			.title {
				font-size: 17px;
				text-align: center;
			}

			.button {
				width: 60%;
				margin: auto;
				margin-top: 60rpx;
				text-align: center;
				color: #ec8131;
				border: 1px solid #ec8131;
				border-radius: 25px;
				font-size: 15px;
				padding: 15rpx 20rpx;
			}
		}

		.bottom {
			position: fixed;
			bottom: 0;
			width: 100%;
			background-color: #fff;
			border-top: 1px solid #f0f0f0;
			text-align: center;
			padding: 30rpx 0;
			color: #ec8131;
			font-size: 38rpx;
		}
	}
</style>
