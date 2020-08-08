<template>
	<div class="searchResult">
		<view class="topInput">
			<view class="leftIcon">
				<uni-icon class="topIcon" type="close" size="23" color="#a4a4a4"></uni-icon>
			</view>
			<view class="centerInput">
				<uni-icon class="topIcon" type="search" size="23" color="#a4a4a4"></uni-icon>
				<input type="text" v-model="inputValue" @input="changeSearch" placeholder-class="phcolor" class="input" placeholder="请输入搜索的商品">
				<uni-icon v-if="showCloseIcon" class="topIcon" type="close" size="23" color="#a4a4a4"></uni-icon>
			</view>
			<view class="rightButton">
				<uni-icon class="topIcon" type="close" size="23" color="#a4a4a4"></uni-icon>
			</view>
		</view>
		<view class="searchShopList">
			<view class="topTitleList">
				<view class="allType">综合</view>
				<view class="sales">销量</view>
				<view class="prices">
					<view class="leftTitle">价格</view>
					<view class="rightIcon">
						<view class="topIcon">^</view>
						<view class="bottomIcon">V</view>
					</view>
				</view>
				<view class="filter">
					<view class="leftTitle">筛选</view>
					<view class="rightIcon">
						<uni-icon class="topIcon" type="close" size="18" color="#000"></uni-icon>
					</view>
				</view>
			</view>
			<view class="noOrder" v-if="ifSearch">
				<view class="shopCartIcon">
					<uni-icon class="topIcon" type="close" size="38" color="#000"></uni-icon>
				</view>
				<view class="bottomTitle">没有找到商品</view>
				<view class="guessYouLike">
					<view class="leftLine"></view>
					<view class="centerTitle">猜你喜欢</view>
					<view class="rightLine"></view>
				</view>
				<view class="guessOrderList">
					<view class"orderMsg" v-for="(item,index) in guessOrderList" :key="index">
						<view class="topPic"></view>
						<view class="orderName">{{item.name}}</view>
						<view class="conditionBlock">
							<view class="condition">{{item.condition}}</view>
							<view class="coupon">{{item.coupon}}</view>
						</view>
						<view class="priceBlock">
							<view class="leftPrice">¥{{item.price}}</view>
							<view class="rightAddToCartButton">
								<uni-icon class="topIcon" type="plus" size="20" color="#fff"></uni-icon>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="searchOrderList" v-else>
				<view class="guessOrderList">
					<view class="orderMsg" v-for="(item,key) in guessOrderList" :key="index">
						<view class="leftPic"></view>
						<view class="rightBlock">
							<view class="orderName">{{item.name}}</view>
							<view class="priceBlock">
								<view class="leftPrice">¥{{item.price}}</view>
								<view class="rightAddToCartButton">
									<uni-icon class="topIcon" type="plus" size="20" color="#fff"></uni-icon>
								</view>
							</view>
						</view>
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
				ifSearch:false,
				inputValue:'',
				showCloseIcon:false,
				guessOrderList: [
				      {
				        id: 1,
				        name: '百事可乐',
				        price: '2',
				        coupon: "满100减101",
				        condition: '限购3件'
				      },
				      {
				        id: 2,
				        name: '维他柠檬茶',
				        price: '345',
				        coupon: "满999减101",
				        condition: '限购3件'
				      },
				      {
				        id: 3,
				        name: '金龙鱼',
				        price: '568',
				        coupon: "满999减101",
				        condition: '限购3件'
				      },
				      {
				        id: 4,
				        name: '金龙鱼',
				        price: '568',
				        coupon: "满999减101",
				        condition: '限购3件'
				      },
				      {
				        id: 5,
				        name: '百事可乐',
				        price: '2',
				        coupon: "满100减101",
				        condition: '限购3件'
				      },
				      {
				        id: 6,
				        name: '维他柠檬茶',
				        price: '345',
				        coupon: "满999减101",
				        condition: '限购3件'
				      },
				      {
				        id: 7,
				        name: '金龙鱼',
				        price: '568',
				        coupon: "满999减101",
				        condition: '限购3件'
				      },
				      {
				        id: 8,
				        name: '金龙鱼',
				        price: '568',
				        coupon: "满999减101",
				        condition: '限购3件'
				      },
				    ]
			}
		},
		methods: {
			changeSearch() {
				if(this.inputValue == '') {
					this.showCloseIcon = false
				} else {
					this.showCloseIcon = true
				}
			}
		},
		components: {
			uniIcon
		}
	}
</script>

<style lang="scss">
	.phcolor {/*placeholder样式*/
	  font-size: 15px;
	}
	.searchResult {
		height: 100%;
		background-color: #f8f8f8;
		.topInput {
			display: flex;
			  align-items: center;
			  justify-content: space-between;
			  padding: 15px 12px;
			  background-color: #fff;
			  border-bottom: 1px solid #ebebeb;
			  .centerInput {
				  display: flex;
				    width: 70%;
				    align-items: center;
				    background-color: #eee;
				    padding: 5px 8px;
				    border: 1px solid #cecece;
				    border-radius: 30px;
					.input {
						margin-left:4rpx;
						width: 100%;
					}
			  }
			  .rightButton {
				  width: 12%;
				    text-align: center;
				    font-size: 17px;
			  }
		}
		.searchShopList {
			.topTitleList {
				display: flex;
				  justify-content: space-around;
				  padding: 30rpx 0;
				  background-color: #fff;
				  font-size: 17px;
				  .prices {
					  display: flex;
					  .rightIcon {
						  margin-left: 8rpx;
						    width: 20px;
						    height: 54rpx;
						    text-align: center;
							.topIcon {
								height: 10px;
							}
							.bottomIcon {
								height: 10px;
								font-size: 14px;
							}
					  }
				  }
				  .filter {
					  display: flex;
					  .rightIcon {
						  margin-left: 8rpx;
					  }
				  }
			}
		}
		.noOrder {
			text-align: center;
			  margin-top: 200rpx;
			  .bottomTitle {
				  margin-top: 30rpx;
				    font-size: 17px;
				    color: #c2c2c2;
			  }
		}
	}
</style>
