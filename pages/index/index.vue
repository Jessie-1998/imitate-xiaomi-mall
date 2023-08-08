<template>
	<view>
		<!-- 顶部选项卡 -->
		<scroll-view scroll-x class="border-bottom scroll-row" style="80rpx">
			<view class="scroll-row-item px-3" style="height: 80rpx;line-height: 80rpx;" v-for="i in 30" :key="i">
				<text class="font-md">{{i}}</text>
			</view>
		</scroll-view>
		<!-- 轮播图组件 -->
		<!-- <swiper-image :resdata="swipers" /> -->
		<!-- 首页分类 -->
		<!-- <index-nav :resdata="indexnavs" /> -->
		<!-- 全局分割线 -->
		<!-- <divider /> -->
		<!-- 三图广告位 -->
		<!-- <three-adv :resdata="threeAdv" /> -->
		<!-- <divider /> -->
		<!-- 大图广告位 -->
		<!-- <card headTitle="每日精选" bodyCover="/static/images/demo/demo4.png" /> -->
		<!-- 公共列表组件 左右372.5upx -->
		<!-- <view class="row j-sb">
			<block v-for="(item,index) in commonList" :key="index">
				<common-list :item="item" :index="index" />
			</block>
		</view> -->
	</view>
</template>

<script>
	import swiperImage from '@/components/index/swiper-image.vue';
	import indexNav from '@/components/index/index-nav.vue';
	import threeAdv from '@/components/index/three-adv.vue';
	import card from '@/components/common/card.vue';
	import commonList from '@/components/common/common-list.vue';
	export default {
		components: {
			swiperImage,
			indexNav,
			threeAdv,
			card,
			commonList
		},
		data() {
			return {
				// 轮播图
				swipers: [{
						src: "/static/images/demo/demo4.png"
					},
					{
						src: "/static/images/demo/demo4.png"
					},
					{
						src: "/static/images/demo/demo4.png"
					}
				],
				// 分类
				indexnavs: [{
						src: "/static/images/indexnav/1.png",
						text: "新品发布"
					},
					{
						src: "/static/images/indexnav/2.gif",
						text: "小米众筹"
					},
					{
						src: "/static/images/indexnav/3.gif",
						text: "以旧换新"
					},
					{
						src: "/static/images/indexnav/4.gif",
						text: "一分换团"
					},
					{
						src: "/static/images/indexnav/5.gif",
						text: "超值特卖"
					},
					{
						src: "/static/images/indexnav/6.gif",
						text: "小米秒杀"
					},
					{
						src: "/static/images/indexnav/7.gif",
						text: "真心想要"
					},
					{
						src: "/static/images/indexnav/8.gif",
						text: "电视热卖"
					},
					{
						src: "/static/images/indexnav/9.gif",
						text: "家电热卖"
					},
					{
						src: "/static/images/indexnav/10.gif",
						text: "米粉卡"
					},
				],
				// 三图广告位
				threeAdv: {
					big: {
						src: "/static/images/demo/demo1.jpg"
					},
					smalltop: {
						src: "/static/images/demo/demo2.jpg"
					},
					smallbottom: {
						src: "/static/images/demo/demo2.jpg"
					}
				},
				// 公共列表
				commonList: [{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				}, {
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				}, {
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				}, {
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				}],
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
</style>