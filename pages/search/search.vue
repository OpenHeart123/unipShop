<template>
	<view>
		<template v-if="newList.length>0">
			<block v-for="(item,index) in newList" :key="index" :style="{height:screenHeight+'px'}">
				<indexList :item="item" :index="index"></indexList>	
			</block>
			<!-- 上拉加载-->
			<load-more :loadText="loadText"></load-more>	
		</template>
		<template v-else-if="isSearch && newList.length<1">
			<no-thing></no-thing>
		</template>
	</view>
</template>

<script>
	import indexList from '../../components/index/index-list.vue';
	import noThing from '../../components/common/no-thing.vue';
	import loadMore from '../../components/common/load-more.vue'
	export default {
		components: {
			indexList,
			loadMore,
			noThing
		},
		data() {
			return {
				isSearch:false,
				loadText: '上拉加载更多',
				newList: [],
				screenHeight:0,
				searchText:''
				
			}
		},
		//监听原生标题栏搜索输入框输入内容变化事件
		onNavigationBarSearchInputChanged(e) {
			this.searchText=e.text
		},
		//监听原生标题栏搜索输入框搜索事件
		onNavigationBarSearchInputConfirmed(e) {
            if(e.text){
				 this.getData(e.text)
				 uni.hideKeyboard()
			}
		},
		onLoad(){
			uni.getSystemInfo({
				success: (res) => {
					this.screenHeight = res.windowHeight;
				}
			});
		},
		//上拉加载
		 onReachBottom(){
			 this.loadMore();
		 },
		 //下拉刷新
		 onPullDownRefresh(){
			 this.getData();
			
		 },
		//监听原生标题栏按钮点击事件
		onNavigationBarButtonTap(e) {
			if (e.index == 0) {
				uni.navigateBack({
					delta: 1
				});
			}
		},
		methods: {
			loadMore() {
				if (this.loadText != "上拉加载更多") {
					return;
				}
				//修改状态
				this.loadText = "加载中。。。";
				//获取数据
				setTimeout(() => {
					let obj = {
						userpic: "../../static/demo/datapic/38.jpg", //头像
						username: "墨尔本",
						isFollow: true,
						title: "世界那么大，我想去看看",
						type: "vedio", //image:图文  vedio:视频
						titlePic: "../../static/demo/datapic/18.jpg",
						playNum: "30w",
						long: "2:56",
						infoNum: {
							index: 1, //0:没有操作，1：顶，2：踩
							agreeNum: 12,
							disAgreeNum: 10
						},
						comments: 33,
						shares: 14
					}
					this.newList.push(obj);
					this.loadText = "上拉加载更多";
				}, 1000)

			},
			//搜索事件
			getData() {
				//请求服务器
				uni.showLoading({
					title:'加载中',
					mask:true
				})
					setTimeout(() => {
						let arr = [{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "鲁大师",
								isFollow: false,
								title: "我用双手成就我的帐本",
								type: "image", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								infoNum: {
									index: 1, //0:没有操作，1：顶，2：踩
									agreeNum: 12,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							},
							{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "墨尔本",
								isFollow: true,
								title: "世界那么大，我想去看看",
								type: "vedio", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								playNum: "30w",
								long: "2:56",
								infoNum: {
									index: 2, //0:没有操作，1：顶，2：踩
									agreeNum: 22,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							},
							{
								userpic: "../../static/demo/datapic/38.jpg", //头像
								username: "墨尔本",
								isFollow: true,
								title: "世界那么大，我想去看看",
								type: "vedio", //image:图文  vedio:视频
								titlePic: "../../static/demo/datapic/18.jpg",
								playNum: "30w",
								long: "2:56",
								infoNum: {
									index: 2, //0:没有操作，1：顶，2：踩
									agreeNum: 22,
									disAgreeNum: 10
								},
								comments: 33,
								shares: 14
							}
						];
						this.newList=this.newList.concat(arr)
						
						uni.stopPullDownRefresh();
						uni.hideLoading();
						this.isSearch=true;
					}, 2000)
				


			}

		}
	}
</script>

<style>

</style>
