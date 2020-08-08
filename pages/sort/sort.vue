<template>
	<div class="sort">
		<view class="topSearchBlock">
			<view class="leftBlock">
				<uni-icon class="shopCartIcon" type="location" size="18" color="#fff"></uni-icon>
				<view class="locationName">深圳市人民政府</view>
				<uni-icon class="arrowIcon" type="forward" size="12" color="#fff"></uni-icon>
			</view>
			<view class="rightInput" @click="toSearch">
				<uni-icon class="topIcon" type="search" size="23" color="#0071ce"></uni-icon>
				<view class="input">请输入搜索的商品</view>
			</view>
		</view>
		<view class="sortBlock">
			<view class="leftOrderList">
				<view class="orderListBlock" @click="showOrderList(index)" v-for="(item,index) in orderList" :key="index">
					<view :class="showId == item.id ? 'leftStyle' : ''"></view>
					<view :class="showId == item.id ? 'orderBlock orderList' : 'orderBlock'">{{item.name}}</view>
				</view>
			</view>
			<view class="rightOrderList">
				<view class="topOrderList">
					<scroll-view scroll-x="true" :scroll-left="navScrollLeft" class="leftOrderBlock">
						<view @click="updatedOrder(index)" v-for="(item,index) in typeList" :key="index" :class="typeIndex == index ? 'orderTypeList active' : 'orderTypeList'">{{item.name}}</view>
					</scroll-view>
					<view class="rightIcon">
						<uni-icon class="rightIcon" type="forward" size="30" color="#0071ce"></uni-icon>
					</view>
				</view>
				<view class="deliverMethod">
					<view class="leftTitle">配送方式</view>
					<view class="rightDeliverList">
						<view class="allButton">全部</view>
						<view class="tomorrowButton">次日达</view>
						<view class="quicklyButton">极速达</view>
					</view>
				</view>
				<view class="bottomOrderList">
					<view class="orderBlock" v-for="(item,index) in orderDetailList" :key="index">
						<view class="leftImg"></view>
						<view class="rightOrderMsg">
							<view class="topTitle">{{item.name}}</view>
							<view class="condition">{{item.condition}}</view>
							<view class="discount">{{item.discount}}</view>
							<view class="priceBlock">
								<view class="leftPrice">
									<view class="currentPrice">¥{{item.currentPrice}}</view>
									<view class="originPrice">¥{{item.originPrice}}</view>
								</view>
								<uni-icon class="addToCart" type="chatboxes" size="15" color="#fff"></uni-icon>
							</view>
						</view>
					</view>
					<view class="bottomBlock"></view>
				</view>
			</view>
		</view>
	</div>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		components: {
			uniIcon
		},
		methods: {
			toSearch() {
				uni.navigateTo({
					url:'../search/search'
				})
			},
			showOrderList(index) { //左侧导航
				this.showId = index + 1
			},
			updatedOrder(index) { //横向导航
				this.typeIndex = index
				let _this = this
				uni.createSelectorQuery().selectAll('.orderTypeList').boundingClientRect((rect) => {
					let allWidth = 0;

					for (let i = 0; i < index; i++) {
						allWidth += rect[i].width
					}

					let sWidth = rect[index].width // 单个view的宽度

					//计算右侧导航的宽度
					uni.createSelectorQuery().select('.leftOrderBlock').boundingClientRect((rect) => {
						let topWidth = 0;
						topWidth = rect.width / 2

						//大于右侧导航宽度的一半开始滚动
						if (allWidth > topWidth) {
							_this.navScrollLeft = allWidth + sWidth / 2 - topWidth
						} else {
							_this.navScrollLeft = 0
						}
					}).exec()
				}).exec()
			}
		},
		data() {
			return {
				typeIndex: 1,
				navScrollLeft: 0, // 顶部滚动条滚动距离
				showId: 1,
				orderDetailList: [{
						id: 1,
						name: '沃尼玛 葡萄 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 2,
						name: '沃尼玛 葡萄 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 3,
						name: '沃尼玛 葡萄 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 4,
						name: '沃尼玛 葡萄 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 5,
						name: '沃尼玛 葡萄 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 6,
						name: '沃尼玛 葡萄 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 7,
						name: '沃尼玛 葡萄 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 8,
						name: '沃尼玛 葡萄 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 9,
						name: '沃尼玛 中性笔 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀9.1折',
						originPrice: '123',
						currentPrice: '223'
					},
					{
						id: 10,
						name: '沃尼玛 玉米 约500G',
						condition: '秒杀价限购2件',
						discount: '秒杀11折',
						originPrice: '33',
						currentPrice: '223'
					},
				],
				typeList: [{
						id: 0,
						name: '全部'
					},
					{
						id: 1,
						name: '纸巾湿巾'
					},
					{
						id: 2,
						name: '锅具'
					},
					{
						id: 3,
						name: '餐具'
					},
					{
						id: 4,
						name: '厨房工具'
					},
					{
						id: 5,
						name: '豆制品'
					}
				],
				orderList: [{
						id: 1,
						name: '火锅节'
					},
					{
						id: 2,
						name: '时令水果'
					},
					{
						id: 3,
						name: '海鲜水产'
					},
					{
						id: 4,
						name: '新鲜蔬菜'
					},
					{
						id: 5,
						name: '肉禽蛋品'
					},
					{
						id: 6,
						name: '火锅节'
					},
					{
						id: 7,
						name: '时令水果'
					},
					{
						id: 8,
						name: '海鲜水产'
					},
					{
						id: 9,
						name: '新鲜蔬菜'
					},
					{
						id: 10,
						name: '肉禽蛋品'
					},
					{
						id: 11,
						name: '火锅节'
					},
					{
						id: 12,
						name: '时令水果'
					},
					{
						id: 13,
						name: '海鲜水产'
					},
					{
						id: 14,
						name: '新鲜蔬菜'
					},
					{
						id: 15,
						name: '肉禽蛋品'
					},
				]
			}
		}
	}
</script>

<style lang="scss">
	/* 选中顶部样式 */
	.active {
		color: #0071ce;
	}

	.sort {
		height: 100vh;

		.topSearchBlock {
			background-color: #0071ce;
			height: 70rpx;
			display: flex;
			justify-content: space-between;
			padding: 20rpx 30rpx;
			color: #fff;

			.leftBlock {
				display: flex;
				align-items: baseline;

				.locationName {
					font-size: 32rpx;
					font-weight: bold;
					margin-top: 5px;
					margin-left: 10rpx;
				}

				.arrowIcon {
					margin-left: 10rpx;
				}
			}

			.rightInput {
				width: 53%;
				display: flex;
				align-items: center;
				padding-left: 10rpx;
				border-radius: 30px;
				background-color: #b3d4f0;

				.input {
					color: #0071ce;
					font-size: 35rpx;
					margin-left: 10rpx;
				}
			}
		}

		.sortBlock {
			display: flex;
			height: 100vh;
			overflow-y: hidden;
		}

		.leftOrderList {
			width: 30%;
			height: 100%;
			overflow-y: auto;

			.orderListBlock {
				text-align: center;
				color: #9c9c9c;
				font-size: 35rpx;
				background-color: #f4f4f4;
				position: relative;
			}

			.orderBlock {
				padding: 30rpx 40rpx;
			}
		}

		.orderList {
			/*点击添加样式*/
			color: #000;
			font-weight: bold;
			background-color: #fff;
		}

		.leftStyle {
			/*点击添加样式*/
			width: 6rpx;
			height: 40rpx;
			position: absolute;
			top: 33%;
			background-color: #0071ce;
		}

		.rightOrderList {
			width: 70%;

			.topOrderList {
				height: 50px;
				overflow: hidden;
				position: relative;
				display: flex;
				border-bottom: 1px solid #ededed;

				.leftOrderBlock {
					height: 57px;
					width: 80%;
					overflow-x: auto;
					background-color: #fff;
					white-space: nowrap;

					.orderTypeList {
						display: inline-block;
						padding: 30rpx;
					}
				}

				.rightIcon {
					background-color: #fff;
					padding: 10rpx 0;
					text-align: center;
					width: 20%;
				}
			}
		}

		.bottomBlock {
			height: 90rpx;
		}

		.deliverMethod {
			display: flex;
			font-size: 26rpx;
			padding: 30rpx 15rpx;

			.leftTitle {
				padding-top: 5rpx;
			}

			.rightDeliverList {
				display: flex;
				margin-left: 20rpx;

				.allButton,
				.tomorrowButton,
				.quicklyButton {
					width: 104rpx;
					border: 1px solid #ebebeb;
					text-align: center;
					border-radius: 20px;
					margin: 5rpx 8rpx;
				}
			}
		}

		.bottomOrderList {
			padding: 0 10px;
			height: 100%;
			overflow-y: auto;

			.orderBlock {
				display: flex;
				align-items: center;
				width: 100%;
			}

			.leftImg {
				width: 160rpx;
				height: 160rpx;
				background-color: red;
			}

			.rightOrderMsg {
				width: 70%;
				padding-bottom: 30rpx;
				border-bottom: 1px solid #ededed;
				margin-left: 10px;

				.condition {
					color: #9b9b9b;
					font-size: 14px;
				}

				.discount {
					font-size: 12px;
					padding: 0 4px;
					background-color: #fef2e8;
					border: 1px solid #ec8131;
					color: #ec8131;
					border-radius: 30px;
					display: inline-block;
				}

				.priceBlock {
					display: flex;
					justify-content: space-between;

					.leftPrice {
						display: flex;
						align-items: center;

						.currentPrice {
							color: #ec8131;
							font-weight: bold;
							font-size: 19px;
						}

						.originPrice {
							color: #9b9b9b;
							margin-left: 10px;
							text-decoration: line-through;
						}
					}

					.addToCart {
						background-color: #ec8131;
						width: 40rpx;
						height: 40rpx;
						line-height: 35rpx;
						border-radius: 50%;
						text-align: center;
					}
				}
			}

			.bottomBlock {
				height: 200rpx;
			}
		}
	}
</style>
