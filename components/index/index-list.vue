<template>
	<view class="index-list animated fadeInLeft fast">
		<view class="index-list1 u-f-ac u-f-jsb">
			<view class="u-f-ac">
				<image :src="item.userpic" mode="widthFix" lazy-load />{{item.username}}
			</view>
			<view class="u-f-ac" v-show="!isFollow" @tap="guanzhu">
				<view class="icon iconfont icon-zengjia">关注</view>
			</view>
		</view>
		<view class="index-list2">
			{{item.title}}
		</view>
		<view class="index-list3 u-f-ajc ">
			<!-- 图片 -->
			<image :src="item.titlePic" mode="widthFix" lazy-load/>
			<template v-if="item.type=='vedio'">
				<!-- 视频 -->
				<view class="icon iconfont icon-bofang index-list3-play">

				</view>
				<view class="index-list3-playInfo">
					{{item.playNum}}次播放量 {{item.long}}
				</view>
			</template>
		</view>
		<view class="index-list4 u-f-jsb u-f-ac">
			<view class="u-f-ac">
				<!-- 顶-->
				<view class="u-f-ac" :class="{'active':infoNum.index===1}" @tap="caozuo('ding')">
					<view class="icon iconfont icon-icon_xiaolian-mian"></view>
					{{infoNum.agreeNum}}
				</view>
				<!-- 踩-->
				<view class="u-f-ac" :class="{'active':infoNum.index===2}" @tap="caozuo('cai')">
					<view class="icon iconfont icon-kulian"></view>
					{{infoNum.disAgreeNum}}
				</view>
			</view>
			<view class="u-f-ac">
				<view class="u-f-ac">
					<view class="icon iconfont icon-pinglun1"></view>
					{{item.comments}}
				</view>
				<view class="u-f-ac">
					<view class="icon iconfont icon-zhuanfa"></view>
					{{item.shares}}
				</view>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		props: {
			item: Object,
			index: Number
		},
		data(){
			 return{
				isFollow:this.item.isFollow,
				infoNum:this.item.infoNum
			 }
		},
		methods: {
			guanzhu(){
				this.isFollow=true;
				uni.showToast({
					title:'关注成功'
				})
			},
			caozuo(type) {
				switch (type) {
					case "ding":
						if (this.infoNum.index == 1) {
							return;
						}
						this.infoNum.agreeNum++;
						if (this.infoNum.index == 2) {
							this.infoNum.disAgreeNum--;
						}
						this.infoNum.index = 1;

						break;
					case "cai":
						if (this.infoNum.index == 2) {
							return;
						}
						this.infoNum.disAgreeNum++;
						if (this.infoNum.index == 1) {
							this.infoNum.agreeNum--;
						}
						this.infoNum.index = 2;
						break;
				}
			}
		}

	}
</script>

<style scoped>
	.index-list {
		padding: 15upx;
		border-bottom: 1upx solid #EEEEEE;
	}

	.index-list1>view:first-child {
		display: flex;
		padding: 10upx;
		color: #969696;
	}

	.index-list1>view:first-child image {
		width: 90upx;
		height: 90upx;
		border-radius: 50%;
		margin-right: 20upx;
	}

	.index-list1>view:last-child {

		background: #F4F4F4;
		border-radius: 4upx;
		padding: 0 10upx;
	}

	.index-list2 {
		margin: 20upx 0;
		font-size: 32upx;
		color: #000000;
		padding-left: 20upx;
	}

	.index-list3 {
		position: relative;
	}

	.index-list3 image {

		width: 100%;
		border-radius: 5upx;
	}

	.index-list3-play {
		position: absolute;
		color: #FFFFFF;
		font-size: 140upx;
	}

	.index-list3-playInfo {
		position: absolute;
		color: #F2F1EF;
		background-color: #4E563A;
		font-size: 20upx;
		padding: 0 10upx;
		border-radius: 16upx;
		bottom: 8upx;
		right: 8upx;
	}

	.index-list4 {
		padding: 15upx 0;
		color: #D5D5D5;

	}

	.index-list4>view:first-child,
	.index-list4>view:last-child {

		padding: 15upx;

	}

	.index-list4>view>view>view,
	.index-list4>view>view:first-child {
		margin-right: 20upx;
	}

	.index-list4 .active,
	.index-list4 .active>view {
		color: #FEDE33;
	}
</style>
