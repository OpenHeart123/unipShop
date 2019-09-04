<template>
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
	  export default {
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
		
	
	
	}
	
	.common-list-r>view:nth-child(4) {
		border-bottom: 1upx solid #EDEDED;
	
	
	}
</style>
