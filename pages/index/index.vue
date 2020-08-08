<template>
	<view class="index">
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
	</view>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		methods: {
			toSearch() {
				uni.navigateTo({
					url:'../search/search'
				})
			},
		},
		components: {
			uniIcon
		}
	}
</script>

<style lang="scss">
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
</style>
