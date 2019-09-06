<template>
	<view class="animated fadeInRight fast">
		<!--自定义导航栏 -->
		<news-nav-bar :tabBars="tabBars" 
					:tabIndex="tabIndex" @tabIndex="changeIndex" 
					@publish="publish"></news-nav-bar>
		<!--动态列表 -->
		<view class="uni-tab-bar">
			   
			<swiper class="swiper-box" 
					:style="{height:screenHeight+'px'}" 
					:current="tabIndex" @change="tapChange">
				<!--关注 -->
				<swiper-item>
					<scroll-view scroll-y class="list" @scrolltolower="loadMore">
						<block v-for="(item,index) in guanzhu.list" :key="index">
							<common-list :item="item" :index="index"></common-list>
						</block>
						<!--上拉加载更多 -->
						<load-more :loadText="guanzhu.loadText"></load-more>
					</scroll-view>
				</swiper-item>
				<!--话题-->
				<swiper-item>
					<scroll-view scroll-y class="list">
						<!--搜索框 -->
						<topic-input/>
						<!-- 轮播图 -->
						<topic-swiper :topicSwiper="topic.topicSwiper"></topic-swiper>						
						<!-- 热门分类-->
						<topic-nav :nav="topic.nav"></topic-nav>
						<!-- 最近更新-->
					    <topic-list :topiclist="topic.topiclist"></topic-list>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>



	</view>
</template>

<script>
	import commonList from '../../components/common/common-list.vue'
	import newsNavBar from '../../components/news/news-nav-bar.vue'
	import loadMore from '../../components/common/load-more.vue'
	import topicNav from '../../components/news/topic-nav.vue'
	import topicSwiper from '../../components/news/topic-swiper.vue'
	import topicList from '../../components/news/topic-list.vue' 
	import topicInput from '../../components/news/topic-input.vue'
	export default {
		components: {
			newsNavBar,
			commonList,
			loadMore,
			topicNav,
			topicSwiper,
			topicList,
			topicInput
			
		},
		data() {
			return {
				tabIndex: 1,
				tabBars: [{
						name: '关注',
						id: 'guanzhu'
					},
					{
						name: '话题',
						id: 'topic'
					}
				],
				screenHeight: 500,
				topic: {
					topicSwiper: [{
							src: '../../static/demo/banner2.jpg'
						},
						{
							src: '../../static/demo/banner2.jpg'
						},
						{
							src: '../../static/demo/banner2.jpg'
						}
					],
					nav: [{
							name: '新闻'
						},
						{
							name: '热门'
						},
						{
							name: '咨询'
						},
						{
							name: '情感'
						},
						{
							name: '旅游'
						},
						{
							name: '电影'
						},
					],
					topiclist:[
						{topicpic:'../../static/demo/datapic/20.jpg',title:'#我是主题大大#',desc:'我是描述',dtnum:33,updatenum:22},
						{topicpic:'../../static/demo/datapic/20.jpg',title:'#我是主题大大2#',desc:'我是描述2',dtnum:23,updatenum:23},
						{topicpic:'../../static/demo/datapic/20.jpg',title:'#我是主题大大3#',desc:'我是描述3',dtnum:43,updatenum:24},
					]
				},

				guanzhu: {
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
		},
		methods: {
			changeIndex(index) {
				this.tabIndex = index;
			},
			//去发布页面
			publish() {
				uni.navigateTo({
					url: '../publish/publish'
				})
			},
			tapChange(e) {
				this.tabIndex = e.detail.current;
			},
			 //加载数据
			loadMore(index) {
				if (this.guanzhu.loadText != "上拉加载更多") {
					return;
				}
				//修改状态
				this.guanzhu.loadText = "加载中。。。";
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
					this.guanzhu.list.push(obj);
					this.guanzhu.loadText = "上拉加载更多";


				}, 1000)


			}



		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					this.screenHeight = res.windowHeight - uni.upx2px(100)
					console.log(this.screenHeight)
				}
			});
		},

	}
</script>

<style>
	
   
</style>
