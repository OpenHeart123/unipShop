<template>
	<view class="home">
		{{msg}}
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg:'我是home组件'
			}
		},
		methods: {
			 
		},
		onLoad(){
			
		}
	}
</script>

<style>
 .home{
	 color: #09BB07;
	 background: #000000;
 }
</style>
