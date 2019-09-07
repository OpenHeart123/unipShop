<template>
	<view class="body">
		<!--tabbar组件 -->
		<swiper-tab-bar 
			:tabBars="tabBars" 
			:tabIndex="tabIndex"
			@tabTap="tabTap" 
			uniSwiperStyle="border-bottom: 0;"
			uniItemStyle="width:33%;">
		</swiper-tab-bar>
		<!--好友列表组件 -->
		  <view class="user-list u-f-ac">
			  <image src="../../static/demo/topicpic/9.jpeg"  lazy-load></image>
			  <view class="u-f-ac u-f-jsb">
				  <view class="user-list-info">
					  <view >昵称</view>
					  <view>
						   <tag-sex-age :item="item"></tag-sex-age>
					  </view> 
				  </view>
				  <view class="icon iconfont icon-xuanze"></view>
			  </view>
		  </view>
	</view>
</template>

<script>
	import swiperTabBar from '../../components/index/swiper-tab-bar.vue';
	import tagSexAge from '../../components/common/tag-sex-age.vue';
	export default {
		components:{
			swiperTabBar,
			tagSexAge
		},
		data() {
			return {
				 item:{
					 age:22,
					 sexIndex:0
				 },
				 tabIndex: 0,
				 tabBars: [{
				 		name: '互关',
				 		id: 'huguan',
						num:12
				 	},
				 	{
				 		name: '关注',
				 		id: 'guanzhu',
						num:22
				 	},
					{
						name: '粉丝',
						id: 'fensi',
						num:33
					}
				 
				 ],
				 
				 
			}
		},
		onNavigationBarButtonTap(e){
			if(e.index==0){
				uni.navigateBack({
					delta: 1
				});
			}
		},
		methods: {
			tabTap(index) {
				this.tabIndex = index;
			},
			
		}
	}
</script>

<style>
	.body{
		padding: 0 20upx;
	}
.user-list{
	padding: 0 20upx;
	border-bottom: 1upx solid #eeeeee;
}
.user-list>image{
	flex-shrink: 0;
	border-radius: 100%;
	width: 100upx;
	height: 100upx;
	margin-right: 20upx;
	margin-bottom: 20upx;
}
.user-list>view:first-of-type{
	  flex: 1;
	  
}
.user-list-info>view:first-child{
	  font-size: 35upx;
	  margin: 10upx 0;
}
.user-list-info>view:last-child{
	
}
.user-list>view:first-of-type>view:last-child{
	color: #CCCCCC;
	font-size: 35upx;
}
</style>
