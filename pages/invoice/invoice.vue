<template>
	<view>
		<uni-segmented-control :current="current" :values="items" style-type="text" @clickItem="onClickItem"></uni-segmented-control>
		<view>
			<view v-show="current === 0">
				<uni-card>
					<text>0.00收入合计</text>
					<text>0.00税额合计</text>
				</uni-card>
				收入发票
			</view>
			<view v-show="current === 1">
				<uni-card>
					<text>0.00支出合计</text>
				</uni-card>
				支出发票
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				items: ['收入发票', '支出发票'],
				current: 0
			}
		},
		methods: {
			onClickItem(e) {
				if (this.current != e.currentIndex) {
					this.current = e.currentIndex;
				}
			}
		}
	}
</script>

<style>

</style>
