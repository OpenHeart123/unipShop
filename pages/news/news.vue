<template>
	<view>
		<!--自定义导航栏 -->
		  <news-nav-bar :tabBars="tabBars" :tabIndex="tabIndex" @tabIndex="changeIndex"></news-nav-bar>
		<!--动态列表 -->
		<block v-for="(item,index) in list" :key="index">
			<common-list :item="item" :index="index"></common-list>
		</block>
	</view>
</template>

<script>
	
	import commonList from '../../components/common/common-list.vue'
	import  newsNavBar from '../../components/news/news-nav-bar.vue'
	export default {
		components: {
			newsNavBar,
			commonList
		},
		
		data() {
			return {
				tabIndex:0,
				tabBars:[
					{name:'关注',id:'guanzhu'},
					{name:'话题',id:'topic'}
				],
				
				
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
			changeIndex(index){
				this.tabIndex=index;
			}
            
		},
		
	}
</script>

<style >
	
	
</style>
