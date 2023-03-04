<template>
	<view>
		<view class="back_a">
			<view>
				<uni-notice-bar show-close="true" show-icon scrollable text="报税期即将截止,请尽快提交数据,以免影响报税!" line>
				</uni-notice-bar>
			</view>
			<uni-card>
				<text class='iconfont icon-qian1'></text>
				<text class="slogan_a">看看本月应交多少钱</text>
				<view class="money">
					<text class="slogan_b">¥</text>
					<text class="amount">{{tax}}</text>
					<text class="slogan_c">预估应交税款（元）</text>
					<image src="../../static/images/icon.png" class="image"></image>
				</view>
			</uni-card>
		</view>
		<view class="nav">
			<view class="nav-item" @click="tostaticstic()">
				<text class='iconfont icon-baobiaotongji'></text>
				<view class="nav-item-title">财务报表</view>
			</view>
			<view class="nav-item" @click="photo()">
				<text class='iconfont icon-paizhao'></text>
				<view class="nav-item-title">快速拍票</view>
			</view>
			<view class="nav-item" @click="toinvoice()">
				<text class='iconfont icon-pingzhengguanli'></text>
				<view class="nav-item-title">查看发票</view>
			</view>
		</view>

		<uni-card title="本期收入" extra="本收入根据税务系统自动同步获得"></uni-card>
		<view>
			<text class="title">财税预警</text>
			<uni-card>
				<uni-list-item title="截止当前日期年度剩余可开发票金额"></uni-list-item>
				<uni-list-item title="自定义右侧插槽" note="列表描述信息" link>
					<template v-slot:footers>
						<image class="slot-image" src="/static/logo.png" mode="widthFix"></image>
					</template>
				</uni-list-item>
			</uni-card>
		</view>

		<view>
			<text class="title">年度单据</text>
			<view class="card_array">
				<uni-card class="card_a">
					<text>开票</text><br>
					<text>-</text><br>
					<text>张数</text><br>
					<text>¥</text>
					<text>0.00</text><br>
					<text>总金额</text>
					<view>-----</view><br>
					<text>收票</text><br>
					<text>-</text><br>
					<text>张数</text><br>
					<text>¥</text>
					<text>0.00</text><br>
					<text>总金额</text>
				</uni-card>
				<view>
					<uni-card>
						<text>工资</text><br>
						<text>¥</text>
						<text>0.00</text><br>
						<text>员工累计收入</text>
					</uni-card>
					<uni-card>
						<text>银行流水</text><br>
						<text>¥</text>
						<text>0.00</text><br>
						<text>交易流水（笔）</text>
					</uni-card>
				</view>
			</view>
		</view>
		<view>
			<camera device-position="back" flash="off" binderror="error"></camera>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src: "",
				tax: "0.0",
			}
		},
		methods: {
			// onInsertDataTap() {
			// 	const db = wx.cloud.database();
			// 	const collection = db.collection('user');
			// 	collection.where({
			// 				username: 'jack',
			// 			}.get({
			// 				success: function(res) {
			// 					this.tax = ""
			// 					console.log(res),
			// 					console.log(tax),
			// 				}
			// 			})
			// 		},
					photo() {
						this.takePhoto()
					},
					takePhoto() {
						var that = this;
						const ctx = uni.createCameraContext();
						ctx.takePhoto({
							quality: 'high',
							success: (res) => {
								console.log(res)
								wx.getFileSystemManager().readFile({
									filePath: res.tempImagePath,
									encoding: 'base64',
									success: res => {
										console.log(res)
										this.setData({
											base64: res.data
										})
									},
									fail: err => {
										this.showToast("调用失败")
									}
								})
							},
							fail: err => {

								this.showToast("调用失败")
							}
						});

					},
					showToast(title) {
						wx.showToast({
							title: title,
							icon: 'none',
							duration: 2500
						})
					},

					tostaticstic() {
						uni.reLaunch({
							url: "/pages/staticstic/staticstic"
						})
					},

					toinvoice() {
						uni.navigateTo({
							url: '/pages/invoice/invoice'
						})

					}
			}
		}
	}
</script>

<style>
	.back_a {

		background: linear-gradient(to bottom, #69b7f3 0%, white 80%);

	}

	.image {
		padding-left: 30%;
		width: 140rpx;
		height: 140rpx;
		margin-top: -10rpx;
		/* box-shadow: 1px 2px 5px #656B79; */
	}

	.slogan_a {
		padding-left: 10rpx;
		color: #69b7f3;
	}

	.slogan_b {
		padding-top: 50rpx;
		padding-left: 10rpx;
		position: absolute;
	}

	.slogan_c {
		padding-top: 90rpx;
		margin-left: -137rpx;
		color: #999999;
		font-size: 24rpx;
	}

	.title {
		padding-left: 2%;
		font-weight: 550;
	}

	.money {
		display: flex;
		position: relative;
		padding-top: 30rpx;
		padding-left: 5rpx;
		height: 150rpx;
	}

	.amount {
		padding-top: 40rpx;
		font-size: 30px;
		font-weight: 500;
		padding-left: 30rpx;

	}

	.card_array {
		display: flex;
		background: linear-gradient(to bottom, #69b7f3 0%, white 80%);
	}

	.card_a {
		font-size: 50rpx;
		width: 350rpx;


	}

	.card_b {
		width: 100rpx;
	}

	.card_c {
		font-size: 50rpx;
		width: 380rpx;
		height: 300rpx;
	}

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
