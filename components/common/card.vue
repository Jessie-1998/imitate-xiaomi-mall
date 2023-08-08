<template>
	<!-- 基础卡片组件 -->
	<view class="card">
		<!-- 标题 -->
		<view class="font-md font-weight p-2 border-bottom main-border-color">
			标题
			</view>
		<!-- body -->
		<view class="">
			<image src="/static/images/demo/demo4.png" mode="widthFix"></image>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			propName: {
				type: Number,
				default: 
			},
		},
	}
</script>

<style>
</style>