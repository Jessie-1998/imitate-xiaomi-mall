<template>
	<!-- 三图广告位 -->
	<!-- 左边w：372 h：530
	右边w：375 h：264 边h2 -->
	<view class="d-flex">
		<image @tap="event(resdata.big)" :src="resdata.big.src" lazy-load style="width: 373upx;height: 530upx;border-right: 2upx solid #F5F5F5;"></image>
		<view class="d-flex flex-column">
			<image @tap="event(resdata.smalltop)" :src="resdata.smalltop.src" lazy-load style="width: 375upx;height: 264upx;border-bottom: 2upx solid #F5F5F5;"></image>
			<image @tap="event(resdata.smallbottom)" :src="resdata.smallbottom.src" lazy-load style="width: 375upx;height: 264upx;"></image>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			resdata:Object
		},
		methods: {
			event(obj) {
				console.log("三图广告",obj)
			}
		},
	}
</script>

<style>
</style>