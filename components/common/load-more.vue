<template>
	<view class="load-text">
		{{loadText}}
	</view>
</template>

<script>
	
	export default {
		props:{
			loadText:String
		}
	}
</script>

<style>
	.load-text {
		color: #aaaaaa;
		text-align: center;
		padding: 16upx;
	}
</style>
