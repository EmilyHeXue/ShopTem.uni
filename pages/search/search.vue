<template>
	<div class="search">
		<view class="topInput">
			<view class="leftInput">
				<uni-icon class="topIcon" type="search" size="23" color="#adadad"></uni-icon>
				<input type="text" v-model="inputValue" @input="changeSearch" placeholder-class="phcolor" class="input" placeholder="请输入搜索的商品">
				<uni-icon v-if="showCloseIcon" class="topIcon" type="close" size="23" color="#adadad"></uni-icon>
			</view>
			<view class="rightButton">取消</view>
		</view>
		<view class="recentSearch">
			<view class="topBlock">
				<view class="leftTitle">最近搜索</view>
				<view class="rightDelete">
					<uni-icon class="topIcon" type="trash" size="25" color="#8c8c8c"></uni-icon>
				</view>
			</view>
			<view class="searchBlock">
				<view @click="toSearchResult" class="search" v-for="(item,index) in searchList" :key="index">{{item.name}}</view>
			</view>
		</view>
		<view class="popularSearch">
			<view class="title">热门搜索</view>
			<view class="searchBlock">
				<view  @click="toSearchResult" class="search" v-for="(item,index) in searchList" :key="index">{{item.name}}</view>
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
			toSearchResult() {//搜索结果
				uni.navigateTo({
					url:'searchResult/searchResult'
				})
			},
			changeSearch() {
				if(this.inputValue == '') {
					this.showCloseIcon = false
				} else {
					this.showCloseIcon = true
				}
			}
		},
		data() {
			return {
				showCloseIcon:false,
				inputValue: '',
				searchList: [{
						id: 1,
						name: '旺仔码头'
					},
					{
						id: 2,
						name: '旺仔码头'
					},
					{
						id: 3,
						name: '旺仔码头'
					},
					{
						id: 4,
						name: '旺仔码头'
					},
					{
						id: 5,
						name: '旺仔码头'
					},
					{
						id: 6,
						name: '果粒橙'
					},
					{
						id: 7,
						name: '雪碧'
					},
					{
						id: 8,
						name: '七喜'
					},
					{
						id: 9,
						name: '可乐'
					},
					{
						id: 10,
						name: '农夫山泉'
					},
				]
			}
		}
	}
</script>

<style lang="scss">
	.phcolor {
		/*placeholder样式*/
		font-size: 15px;
	}

	.topInput {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 15px 12px;
		border-bottom: 1px solid #ebebeb;

		.leftInput {
			display: flex;
			width: 80%;
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

		.rightButton {
			width: 12%;
			text-align: center;
			font-size: 17px;
		}
	}

	.recentSearch {
		padding: 15px 12px;

		.topBlock {
			display: flex;
			justify-content: space-between;
		}

		.searchBlock {
			display: flex;
			flex-wrap: wrap;
			margin-top: 30rpx;

			.search {
				padding: 15rpx;
				margin-right: 20rpx;
				margin-bottom: 20rpx;
				border-radius: 15px;
				background-color: #efefef;
				color: #5d5d5d;
			}
		}
	}

	.popularSearch {
		padding: 15px 12px;

		.searchBlock {
			display: flex;
			flex-wrap: wrap;
			margin-top: 30rpx;

			.search {
				padding: 15rpx;
				margin-right: 20rpx;
				margin-bottom: 20rpx;
				border-radius: 15px;
				background-color: #efefef;
				color: #5d5d5d;
			}
		}
	}
</style>
