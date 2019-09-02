<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
    @import './common/uni.css';
	/*导入字体图标*/
	@import './common/icon.css';
	/*导入animate动画库*/
	@import './common/animate.css';
	/*导入公共的样式库*/
	@import './common/common.css';
</style>
