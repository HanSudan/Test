<template>
	<view id="mine">
		<view class="header">
			<view>
				<image class="image" src="../../static/images/avatar.png"></image>
				<text class="name" @click="login()">点此登录</text>
			</view>
			<!-- <view class="nav">
				<view class="nav-item">
					<view>0</view>
					<view class="nav-item-title">余额</view>
				</view>
				<view class="nav-item">
					<view>0</view>
					<view class="nav-item-title">余额</view>
				</view>
				<view class="nav-item">
					<view>0</view>
					<view class="nav-item-title">余额</view>
				</view>
			</view> -->
		</view>

		<uni-list>
			<uni-list-item title="意见反馈" :show-extra-icon="true" :extra-icon="extraIcon1" showArrow="true"
				clickable="true" @click="feedback()"></uni-list-item>
			<uni-list-item title="关于我们" :show-extra-icon="true" :extra-icon="extraIcon2" showArrow="true">
			</uni-list-item>
			<uni-list-item title="退出登录" :show-extra-icon="true" :extra-icon="extraIcon3" showArrow="true"
				clickable="true" @click="signout()"></uni-list-item>
		</uni-list>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				extraIcon1: {
					type: 'mail-open',
					size: '24px'
				},
				extraIcon2: {
					type: 'staff',
					size: '24px'
				},
				extraIcon3: {
					type: 'close',
					size: '24px'
				},
			}
		},
		methods: {
			feedback(){
				uni.navigateTo({
					url:"../option_feedback/option_feedback"
				})
			},
			signout(){
				uni.showModal({
					title: '提示',
					content: '是否要退出登录?',
					success: function(res) {
						if (res.confirm) {
							uni.reLaunch({
								url: "../login/login"
							})
							// uni.removeStorageSync('name');
						} else if (res.cancel) {
							console.log('用户点击取消');
						}
					}
				});
				
			}
		}
	}
</script>

<style>
	#mine {
		width: 100%;
		height: 100%;
		background: #f3f3f3;
	}

	.header {
		display: flex;
		width: 100%;
		height: 200rpx;
		background-color: #69b7f3;
		position: relative
	}

	.image {
		width: 140rpx;
		height: 140rpx;
		border-radius: 50%;
		margin-top: 30rpx;
		position: absolute;
		margin-left:50rpx;
		margin-top: 30rpx;
	}

	.name {
		position:absolute;
		font-size: 30rpx;
		color: #f3f3f3;
		padding-top: 100rpx;
		padding-left:300rpx;
	}

	
</style>
