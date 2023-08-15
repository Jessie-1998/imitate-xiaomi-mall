<template>
	<view>
		<!-- 顶部选项卡 -->
		<scroll-view scroll-x class="border-bottom scroll-row" style="height:80rpx" :scroll-into-view="scrollinto"
			:scroll-with-animation="true">
			<view @tap="changeTab(index)" class="scroll-row-item px-3" :class="tabIndex===index?'main-text-color':''"
				style="height: 80rpx;line-height: 80rpx;" v-for="(item,index) in tabBars" :key="index"
				:id="'tab'+index">
				<text class="font-md">{{item.name}}</text>
			</view>
		</scroll-view>
		<swiper @change="onChangeTab" :duration="150" :current="tabIndex" :style="'height:' +scrollH+'px;'">
			<swiper-item v-for="(item,index) in newsItems" :key="index">
				<scroll-view @scrolltolower="loadMore(index)" scroll-y="true" :style="'height:' +scrollH+'px;'">
					<block v-for="(list,listIndex) in item.list" :key="listIndex">
						<!-- 轮播图组件 -->
						<swiper-image v-if="list.type==='swipers'" :resdata="list.data" />
						<!-- 首页分类 -->
						<template v-else-if="list.type==='indexnavs'">
							<index-nav :resdata="list.data" />
							<!-- 全局分割线 -->
							<divider />
						</template>
						<template v-else-if="list.type==='threeAdv'">
							<!-- 三图广告位 -->
							<three-adv :resdata="list.data" />
							<divider />
						</template>
						<!-- 大图广告位 -->
						<!-- <card headTitle="每日精选" bodyCover="/static/images/demo/demo4.png" /> -->
						<!-- 公共列表组件 左右372.5upx -->
						<view v-else-if="list.type==='commonList'" class="row j-sb">
							<block v-for="(item2,index2) in list.data" :key="index2">
								<common-list :item="item2" :index="index2" />
							</block>
						</view>
					</block>
					<!-- 上拉加载更多 -->
					<divider />
					<view class="d-flex a-center j-center text-light-muted font-md py-3">
						{{item.loadText}}
					</view>
				</scroll-view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	let demoTabBars = [{
			name: "关注"
		},
		{
			name: "推荐"
		},
		{
			name: "体育"
		},
		{
			name: "热点"
		},
		{
			name: "财经"
		},
		{
			name: "娱乐"
		},
		{
			name: "军事"
		},
		{
			name: "历史"
		},
		{
			name: "本地"
		}
	];
	let demo1 = [{
			type: "swipers", // 轮播图
			data: [{
					src: "/static/images/demo/demo4.png"
				},
				{
					src: "/static/images/demo/demo4.png"
				},
				{
					src: "/static/images/demo/demo4.png"
				}
			],
		},
		{
			type: "indexnavs", // 分类
			data: [{
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
		},
		{
			type: "threeAdv", // 三图广告位
			data: {
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
		},
		{
			type: "commonList", // 公共列表
			data: [{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				},
				{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				},
				{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				},
				{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				}
			],
		}
	]
	let demo2 = [{
			type: "indexnavs", // 分类
			data: [{
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
		},
		{
			type: "threeAdv", // 三图广告位
			data: {
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
		},
		{
			type: "commonList", // 公共列表
			data: [{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				},
				{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				},
				{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				},
				{
					cover: "/static/images/demo/list/1.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					pprice: 1399
				}
			],
		}
	]
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
				scrollH: 500,
				tabIndex: 0, // 当前选中项
				scrollinto: "tab0",
				// 顶部选项卡数据
				tabBars: [],
				// 选项卡对应的页面
				newsItems: []
			}
		},
		onLoad() {
			// 获取可视区域高度
			uni.getSystemInfo({
				success: (res) => {
					this.scrollH = res.windowHeight - uni.upx2px(82)
				}
			})
			// 初始化事件
			this.__init()
		},
		methods: {
			// 初始化事件
			__init() {
				// 获取顶部选项卡
				this.tabBars = demoTabBars
				// 根据顶部选项卡生成页面
				let arr = []
				for (var i = 0, len = this.tabBars.length; i < len; i++) {
					let obj = {
						list: [],
						// 1.上拉加载更多；2.加载中...；3.没有更多了
						loadText: "上拉加载更多"
					}
					// 获取首屏数据
					if (i === 0) {
						obj.list = demo1
					}
					arr.push(obj)
				}
				this.newsItems = arr
			},
			// 加载数据
			addData() {
				// 拿到当前索引
				let index = this.tabIndex
				// 请求数据库
				this.newsItems[index].list = demo2
			},
			// 切换选项卡
			changeTab(index) {
				if (this.tabIndex === index) {
					return;
				}
				this.tabIndex = index
				this.scrollinto = 'tab' + index
				this.addData()
			},
			// 监听滑动列表
			onChangeTab(e) {
				this.changeTab(e.detail.current)
			},
			// 上拉加载更多
			loadMore(index) {
				let item = this.newsItems[index]
				// 是否处于可加载状态
				if (item.loadText !== '上拉加载更多') {
					return;
				}
				// 模拟加载
				item.loadText = '加载中...'
				setTimeout(() => {
					// 加载数据
					item.list = [...item.list, ...demo2]
					// 恢复状态
					item.loadText = '上拉加载更多'
				}, 2000);
			},
		}
	}
</script>

<style>
</style>