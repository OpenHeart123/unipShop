<template>
	<view >
		 <uni-nav-bar :fixed="true" :statusBar="true" @click-right="publish" :border="false"  class="nav-bar-hearder">
		 	<block solt="left">
		 		<view class="tab-bar-left u-f-ajc">
		 			<view class="icon iconfont icon-qiandao"></view>
		 		</view>
		 	</block>
		 	<view class="tab-bar-title u-f-ajc">
		 		 <block v-for="(tab,index) in tabBars" :key="tab.id">
		 			  <view class="u-f-ajc" :class="{'active': tabIndex==index}"   
					        @tap="changeIndex(index)">
		 			     <view class=""> {{tab.name}} </view>
		 			     <view class="tab-bar-bottom-line" v-if="tabIndex==index"></view>
		 			  </view>
		 		 </block>
		 		
		 	</view>
		 	<block solt="right">
		 		<view class="tab-bar-right u-f-ajc" >
		 			<view class="icon iconfont icon-bianji1"></view>
		 		</view>
		 	</block>
		 </uni-nav-bar>
	</view>
	
	
</template>

<script>
	 import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue';
	  export default {
	  	  components:{
			  uniNavBar
		  },
		  props:{
			  tabIndex:Number,
			  tabBars:Array
		  },
		 
		  methods:{
			changeIndex(index){
			   // this.tabIndex=index;	
				 this.$emit('tabIndex',index)
			  },
			  publish(){
			  	console.log('addinput')
			     this.$emit('publish')
			  		
			  }
			
		  }
	  }
</script>
    
<style scoped>
	.nav-bar-hearder {
		position: relative;	
	}
	
	.tab-bar-left {
		color: #FFC583;
		 left: 20upx; 
	
	}
	
	.tab-bar-right {
		color: #333333;
		right: 20upx;	
	}
	
	.tab-bar-left,
	.tab-bar-right {
		position: absolute;
	}
	
	.icon-qiandao,
	.icon-bianji1 {
		font-size: 45upx;
	}
	.tab-bar-title{
		position: absolute;
		
		margin-left: 150upx;
		
	}
	
	.tab-bar-title>view {
		display: flex;
		
		flex-direction: column;
		height: 100%;
		margin: 0 5upx;
		font-size: 35upx;
		font-weight: bold;
		color: #969696;
	}
	
	.tab-bar-bottom-line {
		width: 70upx;
		height: 10upx;
		margin-bottom:-10x;
		border-radius: 20upx;
		background: #FEDE33;
	}
	
	.tab-bar-title .active {
		color: #000000;
	}
	
</style>
