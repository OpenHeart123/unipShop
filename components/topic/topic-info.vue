<template>
	  <view >
	  	  <!--背景图 -->
	  	  <view class="topic-bg">
	  	  	<image :src="item.userPic" mode="aspectFill" lazy-load></image>
	  	  </view>
	  	  <!--详情信息 -->
	  	  <view class="topic-info ">
	  	  	 <view class="topic-info-t u-f-ac">
	  	  		 <image :src="item.userPic" mode="widthFix" lazy-load></image>
	  	  		 <view>#{{item.title}}#</view>
	  	  	 </view>
	  	  	 <view class="topic-info-c u-f-ac">
	  	  		  <view >动态 {{item.dtnum}} </view>
	  	  		  <view >今日 {{item.updatenum}}</view>
	  	  	 </view>
	  	  	 <view class="topic-info-b">{{item.desc}}</view>
	  	  </view>
	  </view>
</template>

<script>
	
	export default {
		props:{
			item:Object
		},	
	}
</script>

<style scoped>
.topic-bg{
	  width: 100%;
	  height: 300upx;
	  position: relative;
	  overflow: hidden;
}
.topic-bg>image{
	  width: 100%;
	  position: absolute;
	  filter: blur(10px);
	   
}
.topic-info{
	  padding: 10upx 20upx 10upx 20upx;
}
.topic-info-t{
	 position: relative;
}
.topic-info-t>image{
	  position: absolute;
	  top:-75upx;
	  width:150upx;
	  height: 150upx;
	  border-radius: 20upx;
	
}
.topic-info-t view{
	  font-size: 35upx;
	  margin-left: 180upx;
	  flex: 1;
}
.topic-info-c{
	  padding: 20upx;
	  
}
.topic-info-c>view{
	  margin-right: 20upx;
	  color: #cdcdcd;
	  font-size: 25upx;
}
.topic-info-b{
	  font-size: 30upx;
	  color: #ababab;
	  padding: 0 15upx;
	 
}
</style>
