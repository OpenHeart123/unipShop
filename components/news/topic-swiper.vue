<template>
	<view >
		<swiper class="topicSwiper"
				:indicator-dots="true" 
				:autoplay="true" 
				:interval="3000" 
				:duration="1000">
			<block v-for="(item,index) in topicSwiper" :key="index">
				<swiper-item>
					<image :src="item.src" mode="widthFix" lazy-load=""></image>
				</swiper-item>
			</block>
		</swiper>
	</view>
</template>

<script>
	  export default {
	  	    props:{
				topicSwiper:Array
			}
	  }
</script>

<style scoped>
	.topicSwiper {
		padding: 0 20upx 20upx 20upx;
	
	}
	
	.topicSwiper image {
		width: 100%;
		border-radius: 20upx;
	}
</style>
