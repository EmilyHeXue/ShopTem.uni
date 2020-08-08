<template>
	<div class="addressList" @touchstart="drawPrint">
		<view class="topBlock"></view>
		<block v-for="(item,index) in data" :key="index">
			<view :style="'transform: translateX('+-item.right+'rpx);transition:0.5s'" class="order-item" @touchend="drawEnd($event,item)"
			 @touchmove="drawMove($event,item)" @touchstart="drawStart($event,item)">
				<view class="addressLeft" >
					<view class="left">
						<view class="topTitle">{{item.address}}</view>
						<view class="bottom">
							<view class="name">{{item.name}}</view>
							<view class="phone">{{item.phone}}</view>
						</view>
					</view>
					<navigator url="editAddress/editAddress?num=1">
						<uni-icon class="rightIcon" type="compose" size="30" color="#999"></uni-icon>
					</navigator>
				</view>
				<view class="remove" @click="stopDraw(item)">
					<view class="removeBlock">
						<uni-icon class="rightIcon" type="trash" size="20" color="#fff"></uni-icon>
						<view class="bottomTitle">删除</view>
					</view>
				</view>
			</view>
		</block>
		<view class="bottomBlock" @click="gotoAddAddress">
			<view class="button">新增收货地址</view>
		</view>
	</div>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {
				delBtnWidth: 160,
				data: [{
					id: 1,
					address: '深圳市福田区',
					name: 'zhang',
					phone: '123456',
					right: 0
				}, {
					id: 2,
					address: '深圳市福田区',
					name: 'aaa',
					phone: '12322456',
					right: 0
				}],
				isScroll: true,
				windowHeight: 0,
				startX: 0
			}
		},
		onLoad() {
			let that = this;
			uni.getSystemInfo({
				success: function(res) {
					that.windowHeight = res.windowHeight;
				}
			})
		},
		components: {
			uniIcon
		},
		methods: {
			stopDraw(item) {//点击删除时不缩回去
				item.right = this.delBtnWidth
			},
			drawPrint() { //点击任意屏幕删除缩回去
				for(let index in this.data) {
					this.data[index].right = 0;
				}
			},
			gotoAddAddress() {
				uni.navigateTo({
					url: './editAddress/editAddress'
				})
			},
			drawStart(e, item) {
				let touch = e.touches[0]

				for(let index in this.data) {
					this.data[index].right = 0;
				}
				this.startX = touch.clientX
			},
			drawMove(e, item) {
				let touch = e.touches[0]
				let disX = this.startX - touch.clientX
				if (disX >= 20) {
					if (disX > this.delBtnWidth) {
						disX = this.delBtnWidth
					}
					item.right = disX
					this.isScroll = false
				} else {
					item.right = 0
					this.isScroll = true
				}
			},
			drawEnd(e, item) {
				if (item.right >= this.delBtnWidth / 2) {
					item.right = this.delBtnWidth
					this.isScroll = true
				} else {
					item.right = 0;
					this.isScroll = true
				}

			}
		}
	}
</script>

<style lang="scss">
	.addressList {
		height: 100vh;
		background-color: #f8f8f8;

		.topBlock {
			height: 1rpx;
		}

		.order-item {
			height: 160rpx;
			width: 100%;
			display: flex;
			position: relative;

			.addressLeft {
				width: 100%;
				background-color: #fff;
				z-index: 5;
				overflow: hidden;
				box-sizing: border-box;
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding: 8px 15px;

				.left {
					.topTitle {
						font-size: 17px;
						color: #282828;
						font-weight: 500;
					}

					.bottom {
						display: flex;
						font-size: 15px;
						color: #6f6f6f;

						.name {
							width: 125rpx;
						}

						.phone {
							margin-left: 10px;
						}
					}
				}
			}
		}

		.bottomBlock {
			position: fixed;
			bottom: 0;
			width: 100%;
			background-color: #fff;
			border-top: 1px solid #efefef;
			padding: 20rpx 0;

			.button {
				color: #fff;
				margin: 5px 20rpx;
				background-color: #1b74ce;
				text-align: center;
				padding: 25rpx 0;
				font-size: 18px;
				font-weight: bold;
				border-radius: 30px;
			}
		}
	}

	.remove {
		width: 160rpx;
		height: 100%;
		background-color: red;
		color: white;
		position: absolute;
		top: 0;
		right: -160rpx;
		text-align: center;

		.removeBlock {
			height: 100%;
			margin-top: 30rpx;
		}
	}

	.order-item:not(:first-child) {
		margin-top: 10px;
	}
</style>
