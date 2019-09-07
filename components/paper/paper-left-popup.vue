<template>
	<view >
		<view class="paper-left-mask" v-if="show" @tap="hiddenPop"></view>
		<view class="paper-left-popup" v-if="show">
			<view class="u-f-ac" hover-class="paper-left-popup-h" @tap="addFriend">
				<view class="icon iconfont icon-sousuo"></view>加糗友
			</view>
			<view class="u-f-ac" hover-class="paper-left-popup-h" @tap="clear">
				<view class="icon iconfont icon-qingchu"></view>清除未读
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			show:Boolean
		},
		methods:{
			hiddenPop(){
				this.$emit("hiddenPop")
			},
			addFriend(){
				this.$emit("addFriend")
			},
			clear(){
				this.$emit("clear")
			}
		}
	}
</script>

<style scoped>
.paper-left-mask{
   position: absolute;
   left: 0;
   right: 0;
   top: 0;
   bottom: 0;
   z-index: 1999;
}
.paper-left-popup{
   position: fixed;
   padding: 20upx;
   background: #ffffff;
   z-index: 2000;
   width: 55%;
   right: 0;
   top: 10upx;
   box-shadow:2upx 2upx 20upx #eeeeee ;
   border-radius: 15upx;
}
.paper-left-popup-h{
   background: #eeeeee;
}
.paper-left-popup>view{
	font-size: 35upx;
}
 .paper-left-popup>view>view{
	font-size: 35upx;
	font-weight: bold;
	margin-right: 20upx;
 }
</style>
