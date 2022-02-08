<template>
	<view class="search-page">
		<u-search :clearabled="true" shape="square" v-model="keywords" :actionText="actionText" @custom="cancel"
			@clickIcon="search" @change="change"></u-search>
		<!-- 搜索结果 -->
		<view class="list-view">
			<view class="label">用户</view>
			<view class="item" v-for="i in 20">
				<view class="item_left">
					<image src="https://img1.baidu.com/it/u=2358365314,1495683115&fm=26&fmt=auto" class="item_avatar">
					</image>
					<view>
						用户名
					</view>
				</view>
				<view class="item_button">发消息</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		onLoad: function(option) {
			// #ifdef APP-NVUE
			this.eventChannel = this.$scope.eventChannel; // 兼容APP-NVUE
			// #endif
			// #ifndef APP-NVUE
			this.eventChannel = this.getOpenerEventChannel();
			// #endif
		},
		beforeDestroy: function() {
			console.log('销毁前');
			this.eventChannel.emit('callback', {
				data: '回调参数'
			});
			this.eventChannel = null;
		},
		data() {
			return {
				eventChannel: null,
				actionText: "取消",
				keywords: ""
			}
		},
		methods: {
			cancel() {
				if(this.actionText === "搜索"){
					console.log("搜索");
				}else{
					console.log("取消");
					uni.navigateBack({
						delta:1
					})
				}
			},
			change(e) {
				console.log("change", e);
				if (e.length > 0) {
					this.actionText = "搜索";
				} else {
					this.actionText = "取消";
				}
			},
			search() {
				console.log("搜索");
			},
		}
	}
</script>

<style lang="scss">
	.search-page {
		padding-top: 20rpx;
		padding-left: 40rpx;
		padding-right: 40rpx;

		.list-view {
			margin-top: 20rpx;
			border-top: 1px solid #e1e1e1;
			padding-top: 20rpx;
			.label{
				font-size: 40rpx;
				font-weight: 700;
				margin-bottom: 10rpx;
			}
			.item {
				display: flex;
				align-items: center;
				justify-content: space-between;
				margin-bottom: 20rpx;
				.item_avatar {
					width: 100rpx;
					height: 100rpx;
					border-radius: 20rpx;
					margin-right: 20rpx;
				}

				.item_left {
					display: flex;
					align-items: center;
					font-weight: 500;
				}

				.item_button {
					background-color: #FFE431;
					font-weight: 500;
					font-size: 30rpx;
					padding-left: 26rpx;
					padding-right: 26rpx;
					padding-top: 6rpx;
					padding-bottom: 6rpx;
					border-radius: 40rpx;
				}
			}
		}
	}
</style>
