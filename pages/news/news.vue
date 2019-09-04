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
			<view class="common-list u-f">
				<view class="common-list-l">
					<image :src="item.userPic" mode="widthFix" v-lazy></image>
				</view>
				<view class="common-list-r">
					<view class="u-f-jsb u-f-ac">
						<view class="u-f-ajc">
							<view class="">{{item.name}}</view>
							<view class="u-f-ajc">
								<view class="tag-sex icon iconfont" :class="[item.sexIndex==0?'icon-nan':'icon-nv']">
									{{item.age}}
								</view>
							</view>

						</view>
						<view class="icon iconfont icon-zengjia" v-show="!item.isFollow">关注</view>
					</view>
					<view>{{item.title}}</view>
					<view class="u-f-ajc">
						<!-- 图片-->
						<image :src="item.titlePic" mode="widthFix" v-lazy v-if="item.titlePic"></image>
						<!-- 视频-->
						<template v-if="item.video">
							<view class="common-list-play icon iconfont icon-bofang"></view>
							<view class="common-list-playinfo">{{item.video.looknum}}次播放 {{item.video.looklong}}</view>
						</template>
                        <!-- 分享-->
                        <view class="common-list-share u-f-ac" v-if="item.share">
                        	<image :src="item.share.titlePic" mode="widthFix" lazy-load></image>
                        	<view class="">{{item.share.title}}</view>
                        </view> 
					</view>					
					<view class="u-f-jsb u-f-ac">
						<view class="">{{item.path}}</view>
						<view class="u-f-ajc">
							<view class="icon iconfont icon-zhuanfa">{{item.sharenum}}</view>
							<view class="icon iconfont icon-pinglun1">{{item.commentnum}}</view>
							<view class="icon iconfont icon-dianzan1">{{item.goodnum}}</view>
						</view>
					</view>
				</view>			
			</view>
	
		</block>
	</view>
</template>

<script>
	import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue'
	export default {
		components: {
			uniNavBar
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

	.common-list {

		padding: 20upx;
	}

	.common-list-l {
		flex-shrink: 0;
	}

	.common-list-l image {
		width: 80upx;
		height: 80upx;
		border-radius: 100%;

	}

	.common-list-r {
		margin: 0 15upx;
		flex: 1;
	}

	.common-list-r>view:nth-child(1)>view:first-child>view:first-child {
		line-height: 25upx;
		font-size: 30upx;
		color: #969696;
		padding: 0 5upx;
	}

	.common-list-r>view:nth-child(1)>view:first-child>view:nth-child(2) {
		width: 80upx;
		background: #81ecec;
		border-radius: 20upx;
		margin-left: 15upx;
	}

	.common-list-r>view:nth-child(1)>view:last-child {
		color: #333333;
		padding: 0 10upx;
		margin-right: 10upx;
		background: #eeeeee;
		font-size: 22upx;
		border-radius: 20upx;
	}

	.tag-sex {
		padding: 2upx 5upx;
		font-size: 30upx;
		line-height: 32upx;
		color: #FFFFFF;

	}

	.common-list-r>view:nth-child(2)>view {
		padding: 15upx 0;
		font-size: 32upx;


	}

	.common-list-r>view:nth-child(2) {
		margin: 15upx 0;
	}

	.common-list-r>view:nth-child(3)>image {
		width: 100%;
		border-radius: 20upx;
	}

	.common-list-r>view:nth-child(3) {
		position: relative;

	}

	.common-list-play,
	.common-list-playinfo {
		position: absolute;
		color: #ffffff;
	}

	.common-list-play {
		font-size: 130upx;
	}

	.common-list-playinfo {
		bottom: 10upx;
		width: 200upx;
		padding: 0 10upx;
		border-radius: 20upx;
		text-align: center;
		right: 10upx;
		font-size: 22upx;
		background: rgba(51, 51, 51, 0.5);
	}

	.common-list-share {
		background: #eeeeee;
		border-radius: 15upx;
		width: 100%;
	}

	.common-list-share image {
		width: 200upx;
		height: 150upx;
		padding: 10upx;
	}

	.common-list-share>view {
		line-height: 30upx;

	}

	.common-list-r>view:nth-child(4)>view {
		color: #BABABA;
		margin-bottom: 10upx;

	}

	.common-list-r>view:nth-child(4)>view:last-child>view {
		margin-left: 6upx;
		padding: 0 3upx;
		letter-spacing: 6upx;


	}

	.common-list-r>view:nth-child(4) {
		border-bottom: 1upx solid #EDEDED;


	}
</style>
