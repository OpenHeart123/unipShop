<template>
	<view>
		<view v-if="item.gstime" class="user-chat-time u-f-ajc">{{item.gstime}}</view>
		<view class="user-chat-body u-f " :class="{'user-chat-me':item.isme}">
				 <image v-if="!item.isme" :src="item.userpic" lazy-load></image>
				 <view class="user-chat-content u-f-ac">
							 <!--文字内容 -->
										 <text v-if="item.type=='text'">{{item.data}}</text>
							 <!--图片内容 -->
							 <image v-if="item.type=='img'" :src="item.data" lazy-load></image>
				 </view>
							 <image  v-if="item.isme" :src="item.userpic" lazy-load></image> 
		</view>
	</view>
</template>

<script>
	 export default{
		 props:{
			 item:Object,
			 index:Number
		 }
	 }
</script>

<style scoped>
.user-chat-time{
	 color: #EEEEEE;
	 font-size: 24upx;
}
.user-chat-body{
	 padding: 15upx;
	 margin-bottom: 20upx;
}
.user-chat-body>image{
	 width: 100upx;
	 height: 100upx;
	 border-radius: 100%;
	 margin-right: 20upx;
	 flex-shrink: 0;
}
.user-chat-content{
	 position: relative;
	 background: #F4F4F4;
	 padding: 10upx 15upx;
	 border-radius: 20upx;
	 font-size: 32upx;
	 color: #000000;
	 
}
.user-chat-content>image{
	 max-width: 150upx;
	 max-height: 200upx;
	 border-radius: 15upx;
	 
}
.user-chat-content:before{
	 content: '';
	 position: absolute;
	 left: -30upx;
	 top: 25upx;
	width: 0;
	 height: 0;
	 border: 16upx solid #F4F4F4;
	 border-color: transparent #F4F4F4 transparent transparent;
		 
}
.user-chat-me{
	 justify-content: flex-end;
}
.user-chat-me>image{
	margin-left: 20upx; 
}
.user-chat-me .user-chat-content:before{
	 left: auto;
	 right: -30upx;
	 border-color: transparent transparent transparent  #F4F4F4;
	 
}
</style>
