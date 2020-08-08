<template>
	<div class="userMsg">
		<div class="userinfo">
			<image class="userinfo-avatar" :src="yonghuwx.avatarUrl"></image>
			<view class="userinfo-name">{{yonghuwx.nickName}}</view>
			<view class="userinfo-phone">{{phone}}</view>
		</div>
		<div class="usermotto">
			<div class="user-motto">{{motto}}</div>
		</div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				yonghuwx: [],
				phone: 123456789,
				motto: '解绑手机号'
			}
		},
		onLoad() {
			let that = this;
			uni.login({
				provider: 'weixin',
				success: function(loginRes) {
					// 获取用户信息				
					uni.getUserInfo({
						provider: 'weixin',
						success: function(infoRes) {
							that.yonghuwx = infoRes.userInfo
						}
					});
				}
			});
		}
	}
</script>

<style lang="scss">
	.userMsg {
		background-color: $blue-bgColor;
		height: 100vh;

		.userinfo {
			display: flex;
			flex-direction: column;
			align-items: center;
			padding-top: 70rpx;

			&-avatar {
				width: 200rpx;
				height: 200rpx;
				margin: 20rpx;
				border-radius: 50%;
			}

			&-name {
				margin-top: 30px;
				font-size: 20px;
				font-weight: bold;
				color: #fff;
			}

			&-phone {
				color: #fff;
				font-weight: bold;
				margin-top: 5px;
			}
		}

		.usermotto {
			margin: 0 auto;
			margin-top: 250px;
			width: 80%;
			text-align: center;
			border: 1px solid #fff;
			border-radius: 30px;
			color: #fff;
			font-weight: bold;
			padding: 10px 0;
		}
	}
</style>
