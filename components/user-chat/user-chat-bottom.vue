<template>
	
		<view class="user-chat-bottom u-f-ac">
			<input type="text" placeholder="请输入消息" class="user-chat-input" v-model="text"/>
			<view class="icon iconfont icon-fabu u-f-ajc" @tap="send" hover-class="user-chat-hover"></view>		
		</view>
	
</template>

<script>
	export default {
		data() {
			return {
				text:""
			};
		},
		methods:{
			send(){
				console.log('send');
				this.$emit('send',this.text)
				this.text=""
			}
		}
	}
</script>

<style scoped>
.user-chat-bottom{
	 position: fixed;
	 border-top: 1upx solid #EEEEEE;
	 left: 0;
	 right: 0;
	 bottom: 0;
	 padding:0upx 20upx;
	 height: 120upx;
	 background: #EEEEEE;
 }
  .user-chat-bottom>input{
	 
	  border-radius: 15upx;
	  margin-right: 10upx;
	  padding: 0 10upx;
	  flex: 1;
	  color: #CDCDCD;
	  background: #FFFFFF;
	  
	  
  }
  .user-chat-bottom>view{
	  width: 80upx;
	  
	  color: yellow;
	  font-size: 50upx;  
  }
  .user-chat-hover{
	  color: #007AFF;
  }
</style>
