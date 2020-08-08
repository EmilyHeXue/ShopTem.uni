<template>
	<div class="cityList">
		<div class="positioningBlock">
			<view class="topTitle">当前定位城市</view>
			<view class="positionCity">点击获取我的位置</view>
		</div>
		<scroll-view :scroll-top="scrollTop" @scroll="scroll" scroll-into-view="jumpNum" scroll-y="true" scroll-with-animation="true">
			<view class="cityListDetail" v-for="(item,index) in city" :key="index">
				<view class="cityTitle">{{item.title}}</view>
				<view class="cityName" v-for="(item2,index2) in item.item" :key="index2">
					{{item2.name}}
				</view>
			</view>
		</scroll-view>
		<view class="rightIndexBlock">
			<view @click="jumpToCity(item)" class="index" v-for="(item,index) in city" :key="index">{{item.title}}</view>
		</view>
	</div>
</template>

<script>
	import City from '../../../../utils/allCity.js'
	export default {
		data() {
			return {
				scrollTop:0,
				city: [],
				jumpNum: ''
			}
		},
		onLoad() {
			this.city = City;
		},
		methods: {
			jumpToCity(item) {
				this.jumpNum = item.title
			},
		}
	}
</script>

<style lang="scss">
	.title {
		padding: 20rpx 0;
		background-color: #f5f5f5;
		color: #9d9d9d;
		font-weight: bold;
		font-size: 17px;
		padding-left: 30rpx;
	}

	.content1 {
		padding: 30rpx 0;
		font-size: 17px;
		padding-left: 30rpx;
		border-bottom: 1px solid #f5f5f5;
	}

	.cityList {
		position: relative;

		.positioningBlock {
			.topTitle {
				@extend .title;
			}

			.positionCity {
				@extend .content1;
			}
		}

		.cityListDetail {
			.cityTitle {
				@extend .title;
			}

			.cityName {
				padding: 30rpx 0;
				font-size: 17px;
				margin-left: 30rpx;
				border-bottom: 1px solid #f5f5f5;
			}
		}

		.rightIndexBlock {
			position: fixed;
			right: 30rpx;
			top: 100rpx;
			text-align: center;
			background-color: #ddd;
			color: #747474;
			font-size: 14px;
			border-radius: 30px;

			.index {
				padding: 6rpx 8rpx;
			}
		}
	}
</style>
