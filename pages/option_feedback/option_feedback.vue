<template>
	<view>
		<view>
			<text class="title">问题和意见</text>
			<view>
				<uni-easyinput type="textarea" class="text_area" placeholder="请输入内容"></uni-easyinput>
			</view>
		</view>
		<view>
			<text class="title">图片(选填)</text>
			<uni-file-picker class="load"></uni-file-picker>
		</view>
		<view >
			<text class="title">联系电话</text>
			<uni-easyinput  class="text_tel" placeholder="方便我们与您联系"></uni-easyinput>
		</view>
		<view>
			<button class="button_submit" @click="feedback()">提交</button>
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
			feedback(){
				uni.showToast({
					title:"提交成功",
					duration:1000,
					success:function(res) {
						uni.reLaunch({
							url: "../my/my"
						})
					}
				})
				
				
			}
		}
	}
</script>

<style>
	.title{
		padding-left: 2%;
		font-weight: 550;
	}
	
	.load{
		padding: 2%;
	}
	
	.button_submit{
		margin-top: 100rpx;
		width: 90%;
		background-color: #006dff;
		color: white;
	}
	
	.text_area{
		padding:2%;
		width:96%;
		font-size: 10rpx;
		display: flex;
		align-items: center;
	}
	.text_tel{
		padding:2%;
		width: 96%;
		font-size: 10rpx;
	}
	
</style>
