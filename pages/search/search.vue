<template>
	<view>
		我是搜索页面
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		//监听原生标题栏搜索输入框输入内容变化事件
		onNavigationBarSearchInputChanged(e){
			console.log(e.text)
		},
		 //监听原生标题栏搜索输入框搜索事件
		onNavigationBarSearchInputConfirmed(e){
			 console.log(e.text)
		},
		//监听原生标题栏按钮点击事件
		onNavigationBarButtonTap(e){
			console.log(JSON.stringify(e))
			if(e.index==0){
				uni.navigateBack({
				    delta: 1
				});
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
