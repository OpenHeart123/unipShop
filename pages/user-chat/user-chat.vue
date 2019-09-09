<template>
	 <view>
		  <!--聊天输入框 -->
		  <scroll-view id="scrollview" scroll-y :scroll-top="scrollTop" 
				:scroll-with-animation="true"
				:style="{height:style.contentH+'px'}">
		  	 <block v-for="(item,index) in list" :key="index">
				   <user-chat-list :item="item" :index="index" class="user-chat-item"></user-chat-list>
		  	 </block>
		  </scroll-view>
		  <!--底部输入框 -->
		  <user-chat-bottom @send="send"></user-chat-bottom>
	 </view>
	 
</template>

<script>
	import userChatBottom from '../../components/user-chat/user-chat-bottom.vue';
	import userChatList from '../../components/user-chat/user-chat-list.vue';
	import time from '../../common/time.js'
	export default {
		components:{
			userChatBottom,
			userChatList
		},
		data() {
			return {
				text:"",
				list:[],
				scrollTop:0,
				style:{
				   contentH	:0,
				   itemH:0
				}
			}
		},
		onLoad(){
			this.getData();
			this.initData();
		},
		onReady(){
			this.pageToBottom();
		},
		methods: {
			send(msg){
			   let nowTime=new Date().getTime();
			   let gstime=time.gettime.getChatTime(nowTime,this.list[this.list.length-1].time)
			   let news=
				   {
				   	isme:true,
				   	userpic:'../../static/demo/datapic/13.jpg',
				   	type:'text',
				   	data:msg,
				   	time:nowTime,
					gstime:gstime
				   }
				 this.list.push(news)
				 //每次发送消息调用一次pageToBottom
				 this.pageToBottom()
			   
			},
			getData(){
				let list=[
					{
						isme:false,
						userpic:'../../static/demo/datapic/13.jpg',
						type:'text',
						data:'我是内容，我是内容',
						time:'1567908683'	
					},
					{
						isme:true,
						userpic:'../../static/demo/datapic/12.jpg',
						type:'img',
						data:'../../static/demo/1.jpg',
						time:'1567908693'
						
					}
				];
				for(let i=0;i<list.length;i++){
					list[i].gstime=time.gettime.getChatTime(list[i].time,i>0?list[i-1].time:0)
				}
				this.list=list			
			},
			initData(){
				try {
				    const res =uni.getSystemInfoSync();				 
				    this.style.contentH=res.windowHeight-uni.upx2px(120)
				} catch (e) {
				    console.log(e)
				}
			},
			pageToBottom(){
				let q=uni.createSelectorQuery().in(this)
				q.select("#scrollview").boundingClientRect()
				q.selectAll(".user-chat-item").boundingClientRect()
				
				q.exec((res)=>{
					res[1].forEach(ret=>{
						this.style.itemH+=ret.height;
					})
					if(this.style.itemH>this.style.contentH){
						this.scrollTop=this.style.itemH
					}
				})
			}
		}
	}
</script>

<style>
 
</style>
