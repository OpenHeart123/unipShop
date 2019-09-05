<template>
	<view class="topic-nav">
		<view class="topic-header u-f-ac u-f-jsb">
			<view class="">热门分类</view>
			<view class="u-f-ajc">更多 <view class="icon iconfont icon-jinru"></view>
			</view>
		</view>
		<view class="topic-content u-f">
			<block v-for="(item,index) in nav" :key="index">
				<view class="u-f-ajc">{{item.name}}</view>
			</block>
		</view>
	</view>
</template>

<script>
	  export default {
	  	 props:{
			 nav:Array
		 }
	  }
</script>

<style scoped>
	.topic-nav {
		padding: 0upx 20upx 20upx 20upx;
		border-bottom: 1upx solid #eeeeee;
		border-top: 1upx solid #eeeeee;
	}

	.topic-header>view:last-child {
		color: #bbbbbb;
		font-size: 28upx;
	}

	.topic-header>view:first-child {
		font-size: 32rpx;

	}

	.topic-header {
		margin-bottom: 20upx;
		margin-top: 20upx;
	}

	.topic-content view {
		background: #eeeeee;
		border-radius: 20upx;
		color: #bebebe;
		margin: 0 10upx;
		flex: 1;
	}
</style>
