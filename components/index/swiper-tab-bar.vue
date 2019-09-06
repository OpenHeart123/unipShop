<template>
	<!--tabBar组件  -->
	<view class="uni-tab-bar">
		<scroll-view scroll-x class="uni-swiper-tab" :style="uniSwiperStyle">
			<block v-for="(tab,index) in tabBars" :key="tab.id">
				<view class="swiper-tab-list" 
				:style="uniItemStyle"
				:class="{'active':tabIndex==index}" @tap="tabTap(index)">{{tab.name}}
					<view class="swiper-tab-line"></view>
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props:{
			tabBars:Array,
			tabIndex:Number,
			uniSwiperStyle:{
				type:String,
				default:""
			},
			uniItemStyle:{
				type:String,
				default:""
			}
		},
		methods: {
			tabTap(index) {
				this.$emit('tabTap',index)
			},
		}
	}
</script>

<style  scoped>
  .swiper-tab-list {
  	color: #969696;
  	font-weight: bold;
  }
  
  .uni-tab-bar .active {
  	color: #343434;
  
  
  }
  
  .active .swiper-tab-line {
  	margin: auto;
  	border-bottom: 6upx solid #FEDE33;
  	width: 70upx;
  	border-radius: 8upx;
  }
  
  .uni-swiper-tab {
  	border-bottom: 1upx solid #EEEEEE;
  }
</style>
