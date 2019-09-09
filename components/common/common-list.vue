<template>
	 <view class="common-list u-f animated fadeInRight fast">
	 	<view class="common-list-l">
	 		<image :src="item.userPic" mode="widthFix" v-lazy></image>
	 	</view>
	 	<view class="common-list-r">
	 		<view class="u-f-jsb u-f-ac">
	 			<view class="u-f-ajc">
	 				<view class="">{{item.name}}</view>
	 				<view class="u-f-ajc">
	 					<tag-sex-age :item="item"></tag-sex-age>
	 				</view>
	 			</view>
	 			<view class="icon iconfont icon-zengjia" v-show="!isFollow" @tap="guanzhu">关注</view>
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
	 	
</template>
       
<script>
	  import tagSexAge from './tag-sex-age';
	  export default {
		  components:{
			  tagSexAge
		  },
	  	    props:{
				item:Object,
				index:Number
			},
			data(){
				return {
					isFollow:this.item.isFollow
				}
			},
			methods:{
				guanzhu(){
					this.isFollow=true;
					 uni.showToast({
					 	title: '关注成功'
					 });
				}
			}
	  }
</script>

<style scoped>
 @import "../../common/list.css";
</style>
