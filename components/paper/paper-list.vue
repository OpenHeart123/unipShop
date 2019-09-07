<template>
	<view class="paper-list u-f-ac animated fadeInLeft fast">
		<image :src="item.userpic"  lazy-load></image>
		<view>
			<view class="u-f-ac u-f-jsb">{{item.username}}
				<view>{{item.time}}</view>
			</view>
			<view class="u-f-ac u-f-jsb">{{item.unreadata}}
				<template v-if="item.unreadnum>0">
					<uni-badge :text="item.unreadnum" type="error" />
				</template>
			</view>
		</view>
	</view>
</template>

<script>
	import uniBadge from '../../components/uni-badge/uni-badge.vue';
	export default {
		components: {
			uniBadge //消息角标组件
		},
		props: {
			item: Object,
			index: Number
		}
	}
</script>

<style scoped>
	.paper-list {
		padding: 10upx 0;
		border-bottom: 1upx solid #eeeeee;
		padding-bottom: 15upx;

	}

	.paper-list>image {
		width: 100upx;
		height: 100upx;
		border-radius: 100%;
		margin-right: 20upx;
		flex-shrink: 0;
	}

	.paper-list>view {
		padding: 10upx 0;
		flex: 1;
	}

	.paper-list>view>view:first-child {
		color: #010101;
		font-size: 32upx;

	}

	.paper-list>view>view>view {
		color: #C4C4C4;
		font-size: 28upx;

	}

	.paper-list>view>view:last-child {
		color: #A3A3A3;
		font-size: 28upx;
		margin-top: 10upx;
	}
</style>
