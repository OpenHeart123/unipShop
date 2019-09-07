<template>
	<view class="u-f-ajc">
		<view class="tag-sex icon iconfont" :class="[item.sexIndex==0?'icon-nan':'icon-nv']">
			{{item.age}}
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object
		}
	}
</script>

<style scoped>
	.tag-sex {
		padding: 2upx 5upx;
		font-size: 30upx;
		line-height: 32upx;
		color: #FFFFFF;
	}
</style>
