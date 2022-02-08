<template>
	<view>
		用户详情
	</view>
</template>

<script>
	export default {
		onNavigationBarButtonTap(e){
			uni.showModal({
				content: e,
				showCancel: false
			});
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">

</style>
