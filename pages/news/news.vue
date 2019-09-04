<template>
	<view>
		<!--自定义导航栏 -->
		<uni-nav-bar :fixed="true" :statusBar="true" @click-right="addInput" class="nav-bar-hearder">
			<block solt="left">
				<view class="tab-bar-left u-f-ajc">
					<view class="icon iconfont icon-qiandao"></view>
				</view>
			</block>
			<view class="tab-bar-title u-f-ajc">
				<view>关注<view class="tab-bar-bottom-line" v-show="false"></view>
				</view>
				<view class="active">话题<view class="tab-bar-bottom-line" v-show="true"></view>
				</view>
			</view>
			<block solt="right">
				<view class="tab-bar-right u-f-ajc">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>
		</uni-nav-bar>
		<!--动态列表 -->
		<block v-for="(item,index) in list" :key="index">
			<common-list :item="item" :index="index"></common-list>
		</block>
	</view>
</template>

<script>
	import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue';
	import commonList from '../../components/common/common-list.vue'
	export default {
		components: {
			uniNavBar,
			commonList
		},
		data() {
			return {
				content: '我是内容，我是内容，我是内容，我是内容，我是内容，我是内容，我是内容，我是内容',
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

		},
		onLoad() {
			if (this.content.length > 25) {
				this.content = this.content.substring(0, 25).concat('......')
			}
		}
	}
</script>

<style>
	.nav-bar-hearder {
		position: relative;
	}

	.tab-bar-left {
		color: #FFC583;
		left: 20upx
	}

	.tab-bar-right {
		color: #333333;
		right: 20upx
	}

	.tab-bar-left,
	.tab-bar-right {

		position: absolute;
	}

	.icon-qiandao,
	.icon-bianji1 {
		font-size: 45upx;
	}

	.tab-bar-title>view {
		display: flex;
		flex-direction: column;
		height: 100%;
		margin: 0 15upx;
		font-size: 35upx;
		font-weight: bold;
		color: #969696;
	}

	.tab-bar-bottom-line {
		width: 70upx;
		height: 10upx;
		margin-top: -10upx;
		border-radius: 20upx;
		background: #FEDE33;
	}

	.tab-bar-title .active {
		color: #000000;
	}

	
</style>
