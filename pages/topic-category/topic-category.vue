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
							<!-- 话题列表-->
							<view class="topic-category">
								<block >
									<topic-list :topiclist="items.list"></topic-list>
								</block>
							</view>
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
	import swiperTabBar from '@/components/index/swiper-tab-bar.vue';
	import topicList from '../../components/news/topic-list.vue';
	import loadMore from '@/components/common/load-more.vue';
	import noThing from '../../components/common/no-thing.vue';
	export default {
		components: {
			swiperTabBar,
			topicList,
			loadMore,
			noThing
		},
		data() {
			return {
				tabIndex: 0,
				screenHeight: 500,
			
				newList: [{
						loadText: '上拉加载更多',
						list: [

							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大#',
								desc: '我是描述',
								dtnum: 33,
								updatenum: 22
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大2#',
								desc: '我是描述2',
								dtnum: 23,
								updatenum: 23
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大3#',
								desc: '我是描述3',
								dtnum: 43,
								updatenum: 24
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大3#',
								desc: '我是描述3',
								dtnum: 43,
								updatenum: 24
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大3#',
								desc: '我是描述3',
								dtnum: 43,
								updatenum: 24
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大3#',
								desc: '我是描述3',
								dtnum: 43,
								updatenum: 24
							},

						]
					},
					{
						loadText: '上拉加载更多',
						list: [

							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大#',
								desc: '我是描述',
								dtnum: 33,
								updatenum: 22
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大2#',
								desc: '我是描述2',
								dtnum: 23,
								updatenum: 23
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大3#',
								desc: '我是描述3',
								dtnum: 43,
								updatenum: 24
							},

						]
					},
					{
						loadText: '上拉加载更多',
						list: [

							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大#',
								desc: '我是描述',
								dtnum: 33,
								updatenum: 22
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大2#',
								desc: '我是描述2',
								dtnum: 23,
								updatenum: 23
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大3#',
								desc: '我是描述3',
								dtnum: 43,
								updatenum: 24
							},

						]
					},
					{
						loadText: '上拉加载更多',
						list: [

							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大#',
								desc: '我是描述',
								dtnum: 33,
								updatenum: 22
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大2#',
								desc: '我是描述2',
								dtnum: 23,
								updatenum: 23
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大3#',
								desc: '我是描述3',
								dtnum: 43,
								updatenum: 24
							},

						]
					},
					{
						loadText: '上拉加载更多',
						list: [

							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大#',
								desc: '我是描述',
								dtnum: 33,
								updatenum: 22
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大2#',
								desc: '我是描述2',
								dtnum: 23,
								updatenum: 23
							},
							{
								topicpic: '../../static/demo/datapic/20.jpg',
								title: '#我是主题大大3#',
								desc: '我是描述3',
								dtnum: 43,
								updatenum: 24
							},

						]
					},



				],
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
							topicpic: '../../static/demo/datapic/20.jpg',
							title: '#我是主题大大#',
							desc: '我是描述',
							dtnum: 33,
							updatenum: 22																
						};
			   			this.newList[index].list.push(obj);
			   			this.newList[index].loadText = "上拉加载更多";
			   
			   
			   		}, 1000)
			   
			   
			   	}
			   

		},
	    onShow() {
	    	uni.getSystemInfo({
	    		success: (res) => {
	    			this.screenHeight = res.windowHeight - uni.upx2px(100)	 
				
					
	    		}
	    	});
	    }, 
	}
</script>

<style>
.topic-category{
	padding: 0 20upx;
}


</style>
