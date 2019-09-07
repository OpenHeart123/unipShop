<template>
	<view>
		<!-- 话题介绍-->
		<topic-info :item="topicinfo"></topic-info>
		<!--tabBar组件-->
		<swiper-tab-bar :tabBars="tabBars" :tabIndex="tabIndex" 
			@tabTap="tabTap" uniSwiperStyle="border-bottom: 0;"
			uniItemStyle="width:50%;"></swiper-tab-bar>
		<!-- 话题详情列表-->
		<view class="topic-detail-list">
			<block v-for="(item,index) in detailist" :key="index">
				<template v-if="tabIndex==index">
					<!--列表 -->
					<block v-for="(itemDetail,detailIndex) in item.list" :key="detailIndex">
						<common-list :item="itemDetail" :index="detailIndex"></common-list>
					</block>
					<!-- 上拉加载-->
					<load-more :loadText="item.loadText">
					</load-more>
				</template>

			</block>
		</view>
	</view>
</template>

<script>
	import topicInfo from '@/components/topic/topic-info.vue';
	import swiperTabBar from '@/components/index/swiper-tab-bar.vue';
	import commonList from '@/components/common/common-list.vue';
	import loadMore from '@/components/common/load-more.vue';
	export default {
		data() {
			return {
				topicinfo: {
					userPic: "../../static/demo/topicpic/13.jpeg",
					title: "敬往事，忆余生",
					dtnum: 222,
					updatenum: 333,
					desc: "我是动态内容我是动态内容"
				},
				tabIndex: 0,
				tabBars: [{
						name: '默认',
						id: '默认'
					},
					{
						name: '最新',
						id: 'zuixin'
					},

				],
				detailist: [
					{
						loadText: '上拉加载更多',
						list: [
							//文字
							{
								userPic: '../../static/demo/topicpic/4.jpeg',
								name: '墨鱼先生',
								age: 25,
								sexIndex: 0, //0 男 1女
								isFollow: false,
								title: '我是标题0',
								titlePic: '',
								video: false,
								share: false,
								path: '深圳 保安',
								sharenum: 20,
								commentnum: 30,
								goodnum: 156
							},
							//图文
							{
								userPic: '../../static/demo/topicpic/4.jpeg',
								name: '晓晓仙女',
								age: 25,
								sexIndex: 0, //0 男 1女
								isFollow: false,
								title: '我是标题1',
								titlePic: '../../static/demo/datapic/2.jpg',
								video: false,
								share: false,
								path: '深圳 福田',
								sharenum: 21,
								commentnum: 32,
								goodnum: 156
							},
							//视频、
							{
								userPic: '../../static/demo/topicpic/4.jpeg',
								name: '开心小子',
								age: 25,
								sexIndex: 1, //0 男 1女
								isFollow: false,
								title: '我是标题2',
								titlePic: '../../static/demo/datapic/2.jpg',
								video: {
									looknum: '20w',
									looklong: '2:32'
								},
								share: false,
								path: '上海 虹桥',
								sharenum: 22,
								commentnum: 33,
								goodnum: 157
							},
							//分享、
							{
								userPic: '../../static/demo/topicpic/4.jpeg',
								name: '流浪歌手',
								age: 25,
								sexIndex: 0, //0 男 1女
								isFollow: false,
								title: '我是标题3',
								titlePic: '',
								video: false,
								share: {
									title: '我是分享标题',
									titlePic: '../../static/demo/datapic/16.jpg'
								},
								path: '北京 天安门',
								sharenum: 25,
								commentnum: 36,
								goodnum: 158
							}
						]
					},
					{
						loadText: '上拉加载更多',
						list: [
							//文字
							{
								userPic: '../../static/demo/topicpic/4.jpeg',
								name: '墨鱼先生',
								age: 25,
								sexIndex: 0, //0 男 1女
								isFollow: false,
								title: '我是标题0',
								titlePic: '',
								video: false,
								share: false,
								path: '深圳 保安',
								sharenum: 20,
								commentnum: 30,
								goodnum: 156
							},
							//图文
							{
								userPic: '../../static/demo/topicpic/4.jpeg',
								name: '晓晓仙女',
								age: 25,
								sexIndex: 0, //0 男 1女
								isFollow: false,
								title: '我是标题1',
								titlePic: '../../static/demo/datapic/2.jpg',
								video: false,
								share: false,
								path: '深圳 福田',
								sharenum: 21,
								commentnum: 32,
								goodnum: 156
							},
							//视频、
							{
								userPic: '../../static/demo/topicpic/4.jpeg',
								name: '开心小子',
								age: 25,
								sexIndex: 1, //0 男 1女
								isFollow: false,
								title: '我是标题2',
								titlePic: '../../static/demo/datapic/2.jpg',
								video: {
									looknum: '20w',
									looklong: '2:32'
								},
								share: false,
								path: '上海 虹桥',
								sharenum: 22,
								commentnum: 33,
								goodnum: 157
							},
							//分享、
							{
								userPic: '../../static/demo/topicpic/4.jpeg',
								name: '流浪歌手',
								age: 25,
								sexIndex: 0, //0 男 1女
								isFollow: false,
								title: '我是标题3',
								titlePic: '',
								video: false,
								share: {
									title: '我是分享标题',
									titlePic: '../../static/demo/datapic/16.jpg'
								},
								path: '北京 天安门',
								sharenum: 25,
								commentnum: 36,
								goodnum: 158
							}
						]
					}
				]

			}
		},
		components: {
			topicInfo,
			swiperTabBar,
			commonList,
			loadMore
		},
		//触底事件，上拉加载
		onReachBottom() {
			this.loadMore();
		},
		//下拉刷新
		onPullDownRefresh() {
			this.getData();
		},
		methods: {
			tabTap(index) {
				this.tabIndex = index;
			},
			getData() {
				//请求数据
				setTimeout(() => {
					//更新数据
					let result = [{
							loadText: '上拉加载更多',
							list: [
								//文字
								{
									userPic: '../../static/demo/topicpic/4.jpeg',
									name: '墨鱼先生111',
									age: 25,
									sexIndex: 0, //0 男 1女
									isFollow: false,
									title: '我是标题0000',
									titlePic: '',
									video: false,
									share: false,
									path: '深圳 保安',
									sharenum: 20,
									commentnum: 30,
									goodnum: 156
								},
								//图文
								{
									userPic: '../../static/demo/topicpic/4.jpeg',
									name: '晓晓仙女dfdf',
									age: 25,
									sexIndex: 0, //0 男 1女
									isFollow: false,
									title: '我是标题1fffff',
									titlePic: '../../static/demo/datapic/2.jpg',
									video: false,
									share: false,
									path: '深圳 福田',
									sharenum: 21,
									commentnum: 32,
									goodnum: 156
								},
								//视频、
								{
									userPic: '../../static/demo/topicpic/4.jpeg',
									name: '开心小子eee',
									age: 25,
									sexIndex: 1, //0 男 1女
									isFollow: false,
									title: '我是标题2fff',
									titlePic: '../../static/demo/datapic/2.jpg',
									video: {
										looknum: '20w',
										looklong: '2:32'
									},
									share: false,
									path: '上海 虹桥',
									sharenum: 22,
									commentnum: 33,
									goodnum: 157
								},
								//分享、
								{
									userPic: '../../static/demo/topicpic/4.jpeg',
									name: '流浪歌手',
									age: 25,
									sexIndex: 0, //0 男 1女
									isFollow: false,
									title: '我是标题3',
									titlePic: '',
									video: false,
									share: {
										title: '我是分享标题',
										titlePic: '../../static/demo/datapic/16.jpg'
									},
									path: '北京 天安门',
									sharenum: 25,
									commentnum: 36,
									goodnum: 158
								}
							]
						},
						{
							loadText: '上拉加载更多',
							list: [
								//文字
								{
									userPic: '../../static/demo/topicpic/4.jpeg',
									name: '墨鱼先生',
									age: 25,
									sexIndex: 0, //0 男 1女
									isFollow: false,
									title: '我是标题0',
									titlePic: '',
									video: false,
									share: false,
									path: '深圳 保安',
									sharenum: 20,
									commentnum: 30,
									goodnum: 156
								},
								//图文
								{
									userPic: '../../static/demo/topicpic/4.jpeg',
									name: '晓晓仙女',
									age: 25,
									sexIndex: 0, //0 男 1女
									isFollow: false,
									title: '我是标题1',
									titlePic: '../../static/demo/datapic/2.jpg',
									video: false,
									share: false,
									path: '深圳 福田',
									sharenum: 21,
									commentnum: 32,
									goodnum: 156
								},
								//视频、
								{
									userPic: '../../static/demo/topicpic/4.jpeg',
									name: '开心小子',
									age: 25,
									sexIndex: 1, //0 男 1女
									isFollow: false,
									title: '我是标题2',
									titlePic: '../../static/demo/datapic/2.jpg',
									video: {
										looknum: '20w',
										looklong: '2:32'
									},
									share: false,
									path: '上海 虹桥',
									sharenum: 22,
									commentnum: 33,
									goodnum: 157
								},
								//分享、
								{
									userPic: '../../static/demo/topicpic/4.jpeg',
									name: '流浪歌手',
									age: 25,
									sexIndex: 0, //0 男 1女
									isFollow: false,
									title: '我是标题3',
									titlePic: '',
									video: false,
									share: {
										title: '我是分享标题',
										titlePic: '../../static/demo/datapic/16.jpg'
									},
									path: '北京 天安门',
									sharenum: 25,
									commentnum: 36,
									goodnum: 158
								}
							]
						}
					];
					this.detailist = result;
					//关闭刷新动画
					uni.stopPullDownRefresh();
				}, 2000);


			},
			loadMore() {
				if (this.detailist[this.tabIndex].loadText != "上拉加载更多") {
					return;
				}
				//修改状态
				this.detailist[this.tabIndex].loadText = "加载中。。。";
				//获取数据
				setTimeout(() => {
					let obj = {
						userPic: '../../static/demo/topicpic/4.jpeg',
						name: '晓晓仙女',
						age: 25,
						sexIndex: 0, //0 男 1女
						isFollow: false,
						title: '我是标题1',
						titlePic: '../../static/demo/datapic/2.jpg',
						video: false,
						share: false,
						path: '深圳 福田',
						sharenum: 21,
						commentnum: 32,
						goodnum: 156
					}
					this.detailist[this.tabIndex].list.push(obj);
					this.detailist[this.tabIndex].loadText = "上拉加载更多";
				}, 1000)


			}

		},

		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					this.screenHeight = res.windowHeight - uni.upx2px(100)
				}
			});
		}
	}
</script>

<style>

</style>
