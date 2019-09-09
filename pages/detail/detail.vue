<template>
	<view>
		<detail-info :item="detail"></detail-info>
	</view>
</template>

<script>
	import detaiInfo from '@/components/detail/detail-info.vue';
	export default {
		components:{
			detaiInfo
		},
		data() {
			return {
				detail:{	userPic: '../../static/demo/topicpic/4.jpeg',
							name: '晓晓仙女',
							age: 25,
							sexIndex: 0, //0 男 1女
							isFollow: false,
							title: '我是标题1',
							titlePic: '../../static/demo/datapic/2.jpg',
							video: false,
							share: false,
							path: '深圳 福田',
							sharenum: 21,
							commentnum: 32,
							goodnum: 156,
					}
			}
		},
		onLoad(e){
           this.initData(JSON.parse(e.detailData))
		    console.log(this.detail)
		},
		onNavigationBarButtonTap(e){
			if(e.index==0){
				console.log('分享')
			}
		},
		
		methods: {
			//初始话导航栏数据
			initData(obj){
				 uni.setNavigationBarTitle({
				 	   title:obj.title
				 })
				
				
			}
			
		}
	}
</script>

<style>

</style>
