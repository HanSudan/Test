<template>
	<view>
		<view class="nav">
			<view class="nav-item" @click="tostaticstic()">
				<text class='iconfont icon-baobiaotongji'></text>
				<view class="nav-item-title">全部发票</view>

			</view>
			<view class="nav-item" @click="photo()">
				<text class='iconfont icon-paizhao'></text>
				<view class="nav-item-title">查看凭证</view>
			</view>
			<view class="nav-item" @click="toinvoice()">
				<text class='iconfont icon-pingzhengguanli'></text>
				<view class="nav-item-title">报税历史</view>
			</view>
			<view class="nav-item" @click="toinvoice()">
				<text class='iconfont icon-pingzhengguanli'></text>
				<view class="nav-item-title">员工工资</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			toinvoice() {
				uni.navigateTo({
					url: '../invoice/invoice'
				})
			},
			tovoucher() {
				uni.navigateTo({
					url: '../voucher/voucher'
				})
			},
		}
	}
</script>

<style>
	.nav {
		margin-top: 50rpx;
		width: 100%;
		display: flex;
	}

	.nav-item {
		flex: 1;
		text-align: center;
		color: #0c0c0c;
	}

	.nav-item-title {
		font-size: 26rpx;
		margin-top: 10rpx;
	}
</style>
