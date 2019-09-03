<template>
	<view>

		<!--自定义导航栏 -->
		<uni-nav-bar :statusBar="true" left-icon="arrowleft" rightText="发布" @click-left="back" @click-right="submit">
			<view class="u-f-ajc" @tap="changeYinsi">
				{{yinsi}}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>

		<!--多行输入框 -->
		<view class="uni-textarea">
			<textarea placeholder="说一句话把~" v-model="text" />
			</view>
		<!--上传多图 -->
		<upload-images @uploud="upload"></upload-images>
	</view>
</template>

<script>
	let yinsi = ['所有人可见', '仅自己可见'];
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	import uploadImages from '../../components/common/upload-images.vue'
	
	
	export default {
		components: {
			uniNavBar,
			uploadImages
		},
		data() {
			return {
				yinsi: '所有人可见',
				text:'',
				title: 'choose/previewImage',
				imageList: [],
			}
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			submit() {
				console.log("发布")
			},
			changeYinsi() {
				uni.showActionSheet({
					itemList: yinsi,
					success: (res)=> {
						 this.yinsi=yinsi[res.tapIndex];
					},
				
				});
			},
			upload(arr){
				this.imageList=arr;
				console.log(this.imageList);
			}
			

	 }
	}
</script>

<style>
  .uni-textarea{
	  border: 1upx solid #eeeeee;
  }
  
</style>
