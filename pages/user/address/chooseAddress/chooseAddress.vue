<template>
	<div class="chooseAddress">
		<view class="topAddressBlock">
			<view class="leftCity" @click="toChooseCity">
				<view class="city">{{city}}</view>
				<uni-icon class="rightIcon" type="forward" size="25" color="#adadad"></uni-icon>
			</view>
			<view class="rightInput">
				<uni-icon class="rightIcon" type="search" size="25" color="#adadad"></uni-icon>
				<input @input="input" v-model="inputValue" type="text" placeholder-class="phcolor" class="input" placeholder="请输入搜索的地址">
				<uni-icon @click="deleteInput" v-if="showCloseIcon" class="rightIcon" type="close" size="25" color="#adadad"></uni-icon>
			</view>
		</view>
		<view class="currentPosition">
			<view class="title">附近地址</view>
			<view class="positionList">
				<view class="positionBlock" v-for="(item,index) in addressList" :key="index">
					<view class="leftBlock">
						<view class="topBlock">
							<view class="currentSign" v-if="index !== 1">[当前位置]</view>
							<view class="topTitle">深圳市市民中心</view>
						</view>
						<view class="bottomAddress">福中三路市民中心B区首层</view>
					</view>
					<view class="rightRepostioning" v-if="index !== 1">
						<uni-icon class="rightIcon" type="location" size="25" color="#0071ce"></uni-icon>
						<view class="rightTitle">重新定位</view>
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
				city: '深圳市',

				inputValue: '',

				showCloseIcon: false,
				addressList: [{
					id: 1,
					bigAddress: '深圳市市民中心',
					detailAddress: '福中三路市民中心B区首层'
				}, {
					id: 2,
					bigAddress: '深圳市中心',
					detailAddress: '福中三路心B区首层'
				}]
			}

		},
		components: {
			uniIcon
		},
		methods: {
			toChooseCity() {
				uni.navigateTo({
					url:'../cityList/cityList'
				})
			},
			input() {
				if (this.inputValue == '') {
					this.showCloseIcon = false
				} else {
					this.showCloseIcon = true
				}
			},
			deleteInput() {
				this.inputValue = '';
				this.showCloseIcon = false
			}
		}
	}
</script>

<style lang="scss">
	.phcolor {
		/*placeholder样式*/
		font-size: 15px;
	}

	.topAddressBlock {
		display: flex;
		justify-content: space-between;
		padding: 10px 20px 10px 12px;

		.leftCity {
			display: flex;
			align-items: center;

			.topIcon {
				margin-left: 6rpx;
			}
		}

		.rightInput {
			display: flex;
			width: 70%;
			align-items: center;
			background-color: #eee;
			padding: 5px 8px;
			border: 1px solid #cecece;
			border-radius: 30px;

			.input {
				margin-left: 4rpx;
				width: 100%;
			}
		}
	}

	.currentPosition {
		.title {
			padding: 10px 15px;
			background-color: #f8f8f8;
			color: #9b9b9b;
		}

		.positionList {
			padding: 0 15px;

			.positionBlock {
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding: 20px 0;
				border-bottom: 1px solid #efefef;

				.leftBlock {
					.topBlock {
						display: flex;

						.currentSign {
							color: #0071ce;
							margin-right: 5px;
						}

						.topTitle {
							font-size: 17px;
							color: #282828;
						}
					}

					.bottomAddress {
						color: #a2a2a2;
						margin-top: 6rpx;
					}
				}

				.rightRepostioning {
					display: flex;

					.rightTitle {
						font-size: 18px;
						color: #0071ce;
					}
				}
			}
		}
	}
</style>
