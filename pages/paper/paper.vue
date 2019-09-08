<template>
	<view class="body">	
		<!-- 菜单按钮开发-->
		 <paper-left-popup :show="show"
		   @hiddenPop="hiddenPop"
		   @addFriend="addFriend"
		   @clear="clear"
		 ></paper-left-popup>
		<!--显示列表 -->
			<block v-for="(item,index) in list" :key="index">
				<paper-list :item="item" :index="index" @tap="gotoChat"/>				
			</block>
			<load-more :loadText="loadText"></load-more>
			
	</view>
</template>

<script>
	import paperList from '../../components/paper/paper-list.vue';
	import loadMore from '../../components/common/load-more.vue';
	import paperLeftPopup  from '../../components/paper/paper-left-popup.vue';
	export default {
		components:{
			paperList,
			loadMore,
			paperLeftPopup
		},
		data() {
			return {
				show:false,
				loadText:'上拉加载更多',
				list:[
					{
						userpic:'../../static/demo/datapic/37.jpg',
						username:'晓晓',
						time:'14：25',
						unreadata:'我是未读的消息',
						unreadnum:22
					},
					{
						userpic:'../../static/demo/datapic/38.jpg',
						username:'晓晓',
						time:'14：25',
						unreadata:'我是未读的消息',
						unreadnum:0
					},{
						userpic:'../../static/demo/datapic/38.jpg',
						username:'晓晓',
						time:'14：25',
						unreadata:'我是未读的消息',
						unreadnum:10
					},
					{
						userpic:'../../static/demo/datapic/38.jpg',
						username:'晓晓',
						time:'14：25',
						unreadata:'我是未读的消息',
						unreadnum:0
					},
					 
					 	{
					 		userpic:'../../static/demo/datapic/37.jpg',
					 		username:'晓晓',
					 		time:'14：25',
					 		unreadata:'我是未读的消息',
					 		unreadnum:22
					 	},
					 	{
					 		userpic:'../../static/demo/datapic/38.jpg',
					 		username:'晓晓',
					 		time:'14：25',
					 		unreadata:'我是未读的消息',
					 		unreadnum:0
					 	},{
					 		userpic:'../../static/demo/datapic/38.jpg',
					 		username:'晓晓',
					 		time:'14：25',
					 		unreadata:'我是未读的消息',
					 		unreadnum:10
					 	},
					 	{
					 		userpic:'../../static/demo/datapic/38.jpg',
					 		username:'晓晓',
					 		time:'14：25',
					 		unreadata:'我是未读的消息',
					 		unreadnum:0
					 	}
				]
			}
		},
		//开启下拉刷新
		 onPullDownRefresh(){
			 this.getData();	
		 },
		 //开启下拉加载
		 onReachBottom(){
			 this.loadMore();
		 },
		 //原生按钮导航栏
		 onNavigationBarButtonTap(e){
			 switch (e.index){
			 	case 0:
				   uni.navigateTo({
				   	    url:'../user-list/user-list'
				   })
				   this.hiddenPop();
			 		break;
				case 1:
					console.log('点击右边的按钮');
					this.showPop();
					break;
			 }
		 },
		methods: {
			
			//跳转到聊天页面
			gotoChat(){
				uni.navigateTo({
					url:"../user-chat/user-chat"
				})
			},
			
			getData(){
				setTimeout(()=>{
					 
				//获取数据
				 let newList=[
						{
							userpic:'../../static/demo/datapic/39.jpg',
							username:'晓晓',
							time:'16：25',
							unreadata:'我是未读的消息',
							unreadnum:2
						},
						{
							userpic:'../../static/demo/datapic/37.jpg',
							username:'晓晓444',
							time:'14：25',
							unreadata:'我是未读的消息',
							unreadnum:0
						},{
							userpic:'../../static/demo/datapic/36.jpg',
							username:'晓晓333',
							time:'14：25',
							unreadata:'我是未读的消息',
							unreadnum:103
						},
						{
							userpic:'../../static/demo/datapic/35.jpg',
							username:'晓晓222',
							time:'14：25',
							unreadata:'我是未读的消息',
							unreadnum:100
						}
					];
				//更新数据
				this.list=newList;
				//关闭刷新
				uni.stopPullDownRefresh();				 
				},2000) 
			
		    },
			loadMore() {
				if (this.loadText != "上拉加载更多") {
					return;
				}
				//修改状态
				this.loadText = "加载中。。。";
				//获取数据
				setTimeout(() => {
					let obj = {
					userpic:'../../static/demo/datapic/37.jpg',
					username:'晓晓',
					time:'14：25',
					unreadata:'我是未读的消息',
					unreadnum:22			
							}
					this.list.push(obj);
					this.loadText = "上拉加载更多";			
				}, 1000)
			
			
			},
		    
			hiddenPop(){
				this.show=false;
			},
			showPop(){
				this.show=true;
			},
			addFriend(){
				this.hiddenPop();
				
			},
			clear(){
				this.hiddenPop();
			}
			
		}
	}
</script>


<style scoped>
   .body{
	   padding: 0 20upx;
   }
   
   
</style>
