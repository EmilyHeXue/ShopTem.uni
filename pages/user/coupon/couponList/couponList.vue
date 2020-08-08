<template>
	<div class="couponCenter">
		<div class="navBar">
			<view @click="menuClick(index)" v-for="(item,index) in titleList" :key="index" :class="[num == index ? 'navBarlist blueActive' : 'navBarlist']">
				<view class="title">{{item.name}}</view>
			</view>
		</div>
		<div class="couponList" v-if="num == 0">
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
				<view class="rightBlock">
					<view class="bottomButton">立即领取</view>
				</view>
			</view>
		</div>
		<div class="couponList" v-if="num == 0">
			<view class="topBlock">
				<view class="leftBlock">
					<view class="left">
						<view class="price">
							<view class="icon">¥</view>
							<view class="number">25</view>
						</view>
						<view class="condition">满199可用</view>
					</view>
					<view class="center">
						<view class="top">【全场券】199减10</view>
						<view class="time">2019.10.31 00:00-2019.10.31 23:59</view>
					</view>
				</view>
				<view class="rightBlock">
					<view class="bottomButton">立即领取</view>
				</view>
			</view>
		</div>
		<div class="noCoupon" v-else>
			<div class="title">还没有优惠券噢</div>
		</div>
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
				}]
			}
		},
		components: {
			uniIcon
		},
		methods: {
			menuClick(index) {
				this.num = index
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

	.couponCenter {
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
				padding-bottom: 20px;

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
					margin-top: 30rpx;
					margin-left: 20rpx;

					.top {
						font-size: 34rpx;
						color: #000;
						font-weight: bold;
					}

					.time {
						font-size: 22rpx;
						margin-top: 15rpx;
						color: #9b9b9b;
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
						padding: 10rpx 15rpx;
						font-size: 28rpx;
						margin-top: 3px;
						border-radius: 30px;
					}
				}
			}
		}

		.noCoupon {
			margin: auto;
			margin-top: 200rpx;
			width: 300rpx;

			.title {
				font-size: 17px;
			}
		}
	}
</style>
