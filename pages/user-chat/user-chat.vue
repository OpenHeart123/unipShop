<template>
	 <user-chat-bottom @send="send"></user-chat-bottom>
</template>

<script>
	import userChatBottom from '../../components/user-chat-bottom.vue';
	export default {
		components:{
			userChatBottom
		},
		data() {
			return {
				text:""
			}
		},
		methods: {
			send(msg){
				console.log(msg)
			}
			
		}
	}
</script>

<style>
 
</style>
