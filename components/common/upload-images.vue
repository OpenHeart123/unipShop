<template>
	<view class="uni-uploader">
	    <view class="uni-uploader-head">
	        <view class="uni-uploader-title">点击可预览选好的图片</view>
	        <view class="uni-uploader-info">{{imageList.length}}/9</view>
	    </view>
	    <view class="uni-uploader-body">
	        <view class="uni-uploader__files">
	            <block v-for="(image,index) in imageList" :key="index">
	                <view class="uni-uploader__file">
						<view class="icon iconfont icon-shanchu" @tap="shanchu(index)"></view>			
	                    <image class="uni-uploader__img" :src="image" :data-src="image" @tap="previewImage"></image>
	                </view>
	            </block>
	            <view class="uni-uploader__input-box">
	                <view class="uni-uploader__input" @tap="chooseImage"></view>
	            </view>
	        </view>
	    </view>
	</view>
	
</template>

<script>
	var sourceType = [
	    ['camera'],
	    ['album'],
	    ['camera', 'album']
	]
	var sizeType = [
	    ['compressed'],
	    ['original'],
	    ['compressed', 'original']
	]
	export default {
		data(){
			return {
				imageList:[],
				sourceTypeIndex: 2,
				sourceType: ['拍照', '相册', '拍照或相册'],
				sizeTypeIndex: 2,
				sizeType: ['压缩', '原图', '压缩或原图'],
				countIndex: 8,
				count: [1, 2, 3, 4, 5, 6, 7, 8, 9]
			}
		},
		methods:{
			shanchu(index){
					uni.showModal({
					    title: '提示',
					    content: '确定要删除该照片吗',
					    success:  (res)=> {
							if(res.confirm){
								 this.imageList.splice(index,1);
								 this.$emit("uploud", this.imageList);
							}
					        
					    },
						
					});
				},
				
			chooseImage: async function() {
				    // #ifdef APP-PLUS
				    // TODO 选择相机或相册时 需要弹出actionsheet，目前无法获得是相机还是相册，在失败回调中处理
				    if (this.sourceTypeIndex !== 2) {
				        let status = await this.checkPermission();
				        if (status !== 1) {
				            return;
				        }
				    }
				    // #endif
				
				    if (this.imageList.length === 9) {
				        return;
				    }
				    uni.chooseImage({
				        sourceType: sourceType[this.sourceTypeIndex],
				        sizeType: sizeType[this.sizeTypeIndex],
				        count: this.imageList.length + this.count[this.countIndex] > 9 ? 9 - this.imageList.length :
				            this.count[this.countIndex],
				        success: (res) => {
				            this.imageList = this.imageList.concat(res.tempFilePaths);
							//选择成功之后向父组件传值
							this.$emit("uploud", this.imageList);
				        },
				        fail: (err) => {
				            // #ifdef APP-PLUS
				            if (err['code'] && err.code !== 0 && this.sourceTypeIndex === 2) {
				                this.checkPermission(err.code);
				            }
				            // #endif
				        }
				    })
				},
			previewImage: function(e) {
				    var current = e.target.dataset.src
				    uni.previewImage({
				        current: current,
				        urls: this.imageList
				    })
				},
		}
	}
</script>

<style>
	.cell-pd {
	    padding: 22upx 30upx;
	}
	
	.list-pd {
	    margin-top: 50upx;
	}
	.uni-uploader__file{
		  position: relative;
	}
	.icon-shanchu{
		  position: absolute;
		  padding: 10upx;
		  background: #34495e;
		  color: #ffffff;
		  border-radius: 10upx;
		  top:0;
		  right: 0;	  
	}
</style>
