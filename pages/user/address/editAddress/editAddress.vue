<template>
	<div class="editAddress">
		<div class="addressBlock">
			<view class="receiptAddress" @click="toChooseAddress">
				<view class="leftBlock">
					<view class="title">收货地址</view>
					<view class="placeHolder">小区/写字楼/学校</view>
				</view>
				<view class="rightBlock">
					<uni-icon class="rightIcon" type="forward" size="25" color="#adadad"></uni-icon>
				</view>
			</view>
			<view class="houseNum">
				<view class="leftBlock">
					<view class="title">门牌号</view>
				</view>
				<view class="rightBlock">
					<input placeholder-class="phcolor" class="input" placeholder="例：8楼290号">
				</view>
			</view>
			<view class="receiver">
				<view class="leftBlock">
					<view class="title">收货人</view>
				</view>
				<view class="rightBlock">
					<input placeholder-class="phcolor" class="input" placeholder="收货人姓名">
				</view>
			</view>
			<view class="phone">
				<view class="leftBlock">
					<view class="title">手机号</view>
				</view>
				<view class="rightBlock">
					<input placeholder-class="phcolor" class="input" placeholder="配送员联系您的手机号码">
				</view>
			</view>
			<view class="label">
				<view class="leftBlock">
					<view class="title">标签</view>
				</view>
			</view>
		</div>
		<view class="submit">保存</view>
		<view class="delete">删除</view>
	</div>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		components: {
			uniIcon
		},
		onLoad(e) {
			if (e.num == 1) {
				uni.setNavigationBarTitle({
					title: '编辑收货地址'
				})
			} else {
				uni.setNavigationBarTitle({
					title: '新增收货地址'
				})
			}
		},
		methods: {
			toChooseAddress() {
				uni.navigateTo({
					url:'../chooseAddress/chooseAddress'
				})
			}
		}
	}
</script>

<style lang="scss">
	.phcolor {
		/*placeholder颜色*/
		color: #cecece;
	}

	.editAddress {
		height: 100vh;
		padding-top: 10px;
		background-color: #f8f8f8;

		.addressBlock {
			background-color: #fff;
			padding-left: 30rpx;

			.receiptAddress {
				border-bottom: 1px solid #ededed;
				padding: 15px 12px 15px 0;
				display: flex;
				justify-content: space-between;

				.leftBlock {
					display: flex;
					align-items: center;

					.title {
						color: #989898;
						width: 175rpx;
						font-size: 17px;
					}

					.placeHolder {
						color: #cecece;
						font-size: 17px;
					}
				}
			}

			.houseNum {
				border-bottom: 1px solid #ededed;
				padding: 15px 12px 15px 0;
				display: flex;
				align-items: center;

				.leftBlock {
					display: flex;

					.title {
						color: #989898;
						width: 175rpx;
						font-size: 17px;
					}
				}
			}

			.receiver {
				border-bottom: 1px solid #ededed;
				padding: 15px 12px 15px 0;
				display: flex;

				.leftBlock {
					display: flex;

					.title {
						color: #989898;
						width: 175rpx;
						font-size: 17px;
					}
				}
			}

			.phone {
				border-bottom: 1px solid #ededed;
				padding: 15px 12px 15px 0;
				display: flex;

				.leftBlock {
					display: flex;

					.title {
						color: #989898;
						width: 175rpx;
						font-size: 17px;
					}

					.placeHolder {
						color: #cecece;
						font-size: 17px;
					}
				}
			}

			.label {
				border-bottom: 1px solid #ededed;
				padding: 15px 12px 15px 0;
				display: flex;
				justify-content: space-between;

				.leftBlock {
					display: flex;

					.title {
						color: #989898;
						width: 175rpx;
						font-size: 17px;
					}
				}
			}
		}

		.submit {
			margin: 20px 12px 0 12px;
			text-align: center;
			padding: 10px 0;
			color: #fff;
			font-size: 17px;
			font-weight: 600;
			background-color: #0071ce;
			border-radius: 30px;
		}

		.delete {
			margin: 15px 12px 0 12px;
			text-align: center;
			padding: 10px 0;
			font-size: 17px;
			color: #4a4a4a;
			border: 1px solid #4a4a4a;
			border-radius: 30px;
		}
	}
</style>
