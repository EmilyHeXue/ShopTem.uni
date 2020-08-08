<template>
	<div class="afterSale">
		<view class="afterSale-topRemind">
			<uni-icon class="afterSale-topRemind-icon" type="paperplane" size="20" color="#999"></uni-icon>
			<view class="afterSale-topRemind-title">订单完成14天后可申请售后</view>
		</view>
		<view class="afterSale-noAfterSale">
			<uni-icon class="afterSale-noAfterSale-icon" type="closeempty" size="40" color="#999"></uni-icon>
			<view class="afterSale-noAfterSale-title">您还未申请过售后</view>
		</view>
	</div>
</template>

<script>
	import uniIcon from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {

			}
		},
		components: {
			uniIcon
		}
	}
</script>

<style lang="scss">
	.afterSale {
		height: 100vh;
		background-color: #fff;
		
		&-topRemind {
			background-color: #e7f1fa;
			display: flex;
			padding: 30rpx;
			align-items: center;
			color: #134772;
		}

		&-noAfterSale {
			text-align: center;
			margin-top: 300rpx;

			&-title {
				margin-top: 40rpx;
				color: #545454;
			}
		}
	}
</style>
