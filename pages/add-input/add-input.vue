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
		
		<!--弹出公告 -->
		  <uni-popup :show="showPopup" position="middle" mode="fixed" @hidePopup="hidePopup">
		  	<view class="gonggao">
		  		<view class="u-f-ajc">
		  			<image src="../../static/common/addinput.png" mode="widthFix"></image>
		  		</view>
		  		<view class="">1、涉及黄色，政治，广告及骚扰信息 </view>
		  		<view class=""> 2、涉及人身攻击</view>
		  		<view class=""> 3、留联系方式，透露他人隐私</view>
		  		<view class="">一经核实将被封禁，情节严重者永久封禁 </view>
		  		<button type="primary" @tap="hidePopup">朕知道了</button>
		  	</view>
		  </uni-popup>
	</view>
</template>

<script>
		let yinsi = ['所有人可见', '仅自己可见'];
		import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue';
		import uploadImages from '@/components/common/upload-images.vue';
		import uniPopup from '@/components/uni-popup/uni-popup.vue';
	export default {
		components: {
			uniNavBar,
			uploadImages,
			uniPopup	
		},
		data() {
			return {
				yinsi: '所有人可见',
				text:'',
				title: 'choose/previewImage',
				imageList: [],
				showPopup:true
			}
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			submit() {
			   this.showPopup=true;
			   console.log('submit')
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
			},
			hidePopup(){
				this.showPopup=false;
			}
						
	 },
	 onLoad(){
		 this.yinsi='所有人可见';
	 }
	}
</script>

<style>
  .uni-textarea{
	  border: 1upx solid #eeeeee;
  }
  .gonggao image {
  	width: 75%;
  	margin-bottom: 15upx;
  } 
  .gonggao {
  	width: 500upx;
  }
  
  .gonggao button {
  	margin-top: 15upx;
  	background-color: #FFE934;
  	color: #000000;
  	font-size: 14px;
  }
 
</style>
