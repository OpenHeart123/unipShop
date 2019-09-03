<template>
	<view>
		<!--tabBar组件-->
		<swiper-tab-bar :tabBars="tabBars" :tabIndex="tabIndex" @tabTap="tabTap"></swiper-tab-bar>
		<!--滑动组件-->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:screenHeight+'px'}" :current="tabIndex" @change="tapChange">
				<swiper-item v-for="(items,index) in newList" :key="index">
					<scroll-view scroll-y class="list" @scrolltolower="loadMore(index)">
						<template v-if="items.list.length>0">
							<!-- 图文列表-->
							<block v-for="(item,index1) in items.list" :key="index1">
								<indexList :item="item" :index="index1"></indexList>
							</block>
							<!-- 上拉加载-->
							<load-more :loadText="items.loadText"></load-more>
						</template>
						<template v-else>
							<!--默认数据 -->
							<no-thing></no-thing>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>


	</view>
</template>

<script>
	import indexList from '@/components/index/index-list.vue';
	import swiperTabBar from '@/components/index/swiper-tab-bar.vue';
	import loadMore from '@/components/common/load-more.vue';
	import noThing from '../../components/common/no-thing.vue'
	export default {
		components: {
			indexList,
			swiperTabBar,
			loadMore,
			noThing
		},
		data() {
			return {
				newList: [{
						loadText: '上拉加载更多',
						list: [{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "鲁大师",
								isFollow: false,
								title: "我用双手成就我的帐本",
								type: "image", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								infoNum: {
									index: 1, //0:没有操作，1：顶，2：踩
									agreeNum: 12,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							},
							{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "墨尔本",
								isFollow: true,
								title: "世界那么大，我想去看看",
								type: "vedio", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								playNum: "30w",
								long: "2:56",
								infoNum: {
									index: 2, //0:没有操作，1：顶，2：踩
									agreeNum: 22,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							},
						]
					},
					{
						loadText: '上拉加载更多',
						list: [{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "鲁大师",
								isFollow: false,
								title: "我用双手成就我的帐本",
								type: "image", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								infoNum: {
									index: 2, //0:没有操作，1：顶，2：踩
									agreeNum: 12,
									disAgreeNum: 22
								},
								comments: 33,
								shares: 14
							},
							{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "墨尔本",
								isFollow: true,
								title: "世界那么大，我想去看看",
								type: "vedio", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								playNum: "30w",
								long: "2:56",
								infoNum: {
									index: 1, //0:没有操作，1：顶，2：踩
									agreeNum: 15,
									disAgreeNum: 13
								},
								comments: 33,
								shares: 14
							},
						]
					},
					{
						loadText: '上拉加载更多',
						list: [{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "鲁大师",
								isFollow: false,
								title: "我用双手成就我的帐本",
								type: "image", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								infoNum: {
									index: 1, //0:没有操作，1：顶，2：踩
									agreeNum: 12,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							},
							{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "墨尔本",
								isFollow: true,
								title: "世界那么大，我想去看看",
								type: "vedio", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								playNum: "30w",
								long: "2:56",
								infoNum: {
									index: 2, //0:没有操作，1：顶，2：踩
									agreeNum: 12,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							},
						]
					},
					{
						loadText: '上拉加载更多',
						list: [{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "鲁大师",
								isFollow: false,
								title: "我用双手成就我的帐本",
								type: "image", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								infoNum: {
									index: 1, //0:没有操作，1：顶，2：踩
									agreeNum: 12,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							},
							{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "墨尔本",
								isFollow: true,
								title: "世界那么大，我想去看看",
								type: "vedio", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								playNum: "30w",
								long: "2:56",
								infoNum: {
									index: 2, //0:没有操作，1：顶，2：踩
									agreeNum: 12,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							},
						]
					},
					{
						loadText: '上拉加载更多',
						list: []
					},



				],
				tabIndex: 0,
				screenHeight: 500,

				tabBars: [{
						name: '关注',
						id: 'guanzhu'
					},
					{
						name: '推荐',
						id: 'tuijian'
					},
					{
						name: '体育',
						id: 'tiyu'
					},
					{
						name: '热点',
						id: 'redian'
					},
					{
						name: '财经',
						id: 'caijing'
					},
					{
						name: '娱乐',
						id: 'yule'
					},
				]
			}
		},
		methods: {
			tabTap(index) {
				console.log(index);
				this.tabIndex = index;
			},
			tapChange(e) {
				this.tabIndex = e.detail.current;
			},
			loadMore(index) {
				if (this.newList[index].loadText != "上拉加载更多") {
					return;
				}
				//修改状态
				this.newList[index].loadText = "加载中。。。";
				//获取数据
				setTimeout(() => {
					let obj = {
						userpic: "../../static/demo/datapic/38.jpg", //头像
						username: "墨尔本",
						isFollow: true,
						title: "世界那么大，我想去看看",
						type: "vedio", //image:图文  vedio:视频
						titlePic: "../../static/demo/datapic/18.jpg",
						playNum: "30w",
						long: "2:56",
						infoNum: {
							index: 1, //0:没有操作，1：顶，2：踩
							agreeNum: 12,
							disAgreeNum: 10
						},
						comments: 33,
						shares: 14
					}
					this.newList[index].list.push(obj);
					this.newList[index].loadText = "上拉加载更多";


				}, 1000)


			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					this.screenHeight = res.windowHeight - uni.upx2px(100)

				}
			});
		},
		//监听搜索栏点击事件
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
				url: '../search/search'
			})
		},
		//监听原生标题栏按钮点击事件
		onNavigationBarButtonTap(e){
			// console.log(JSON.stringify(e))
			if(e.index==1){
				uni.navigateTo({
					url: '../add-input/add-input',
				});
			}
		},



	}
</script>

<style>
	
</style>
