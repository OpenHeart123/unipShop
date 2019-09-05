<template>
	<view class="topic-news">
		<view class="topic-title">最近更新</view>
		<block v-for="(item,index) in topiclist" :key="index">
			<view class="topic-list u-f-ac">
				<image  :src="item.topicpic" 
						mode="widthFix" lazy-load></image>
				<view class="topic-list-desc">
					<view>{{item.title}}</view>
					<view>{{item.desc}}</view>
					<view>动态 {{item.dtnum}} 更新 {{item.updatenum}}</view>
				</view>
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		props:{
			topiclist:Array
		}
	}
</script>

<style scoped>
.topic-news{
	padding: 20upx;
}
.topic-title{
	font-size: 32upx;		
}
.topic-list{
	border-bottom:1upx solid #cccccc;
	opacity: 0.8;
	padding-bottom: 20upx;
	padding-top: 20upx;
}
.topic-list image{
	width:  200upx;
	height: 200upx;
	border-radius: 10upx;
	margin-right: 20upx;
}

.topic-list-desc>view{
	font-size: 28upx;
	color: #bbbbbb;
	line-height: 40upx;
		
}
.topic-list-desc>view:first-child{
	color: #333333;
	font-size: 32upx;
}
</style>
