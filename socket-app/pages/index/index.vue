<template>
	<view class="index_page">
		<!-- 头部导航 -->
		<view class="app_bar">
			<view class="size_box"></view>
			<view class="container">
				<image class="app_avatar" :src="userInfo.avatar"></image>
				<image class="app_avatar" src="/static/images/logo.png"></image>
				<view class="actions">
					<image class="actions_icon" src="/static/images/search.png" @click="clickHandle('search')"></image>
					<view style="width: 20rpx;"></view>
					<image class="actions_icon" src="/static/images/add.png"></image>
				</view>
			</view>
		</view>
		<!-- 列表区域 -->
		<view class="list_view">
			<view class="item" v-for="i in 20" @click="clickHandle('chat')">
				<view class="realtive" @click.stop="clickHandle('detial')">
					<image class="item_cover" :src="userInfo.avatar"></image>
					<view class="badge">
						7
					</view>
				</view>
				<view class="item_content">
					<view class="item_title">
						<view>好友请求</view>
						<view class="time">10:05</view>
					</view>
					<view>开发的实例似懂非懂</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo: {
					avatar: "https://img2.baidu.com/it/u=3804069081,3968854353&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500"
				},
				title: 'Hello所得税法定',
			}
		},
		onLoad() {
			console.log('onload')
		},
		methods: {
			// 创建socket连接
			initSocket() {
				console.log('创建socket连接')
				uni.connectSocket({
					url: 'http://127.0.0.0:3000',
					data: {
						x: '',
						y: ''
					},
					header: {
						'content-type': 'application/json'
					},
					protocols: ['protocol1'],
					method: "GET"
				});
			},
			clickHandle(type) {
				switch (type) {
					case 'search':
						uni.navigateTo({
							url: "/pages/search/search",
							events: {
								// 为指定事件添加一个监听器，获取被打开页面传送到当前页面的数据
								callback: function(data) {
									console.log("接收的回调参数", data)
								},
							},
						})
						break;
					case 'chat':
						uni.navigateTo({
							url: "/pages/chatPage/chatPage",
						})
						break;
					case 'detial':
						uni.navigateTo({
							url: "/pages/userInfo/userInfo",
						})
						break;
				}
			}
		}
	}
</script>

<style lang="scss">
	$bar_heifht:100rpx;

	.index_page {
		.realtive {
			position: relative;
		}

		.app_bar {
			padding-top: var(--status-bar-height);

			.size_box {
				height: 120rpx;
				width: 100%;
				// background-color: yellow;
			}

			.container {
				display: flex;
				justify-content: space-between;
				align-items: center;
				padding-top: 10rpx;
				padding-bottom: 10rpx;
				padding-left: 40rpx;
				padding-right: 40rpx;
				background-color: white;
				position: fixed;
				top: 0;
				left: 0;
				// background-color: red;
				right: 0;
				height: 100rpx;
				z-index: 9999;

				.app_avatar {
					width: 80rpx;
					height: 80rpx;
					border-radius: 10rpx;
				}

				.app_actions {
					width: 160rpx;
					background-color: red;
					display: flex;
				}

				.actions_icon {
					height: 80rpx;
					width: 80rpx;
				}

				.actions {
					display: flex;
				}
			}
		}

		.list_view {
			// background-color: blue;
			padding: 20rpx;

			.item {
				display: flex;
				margin-bottom: 20rpx;

				.badge {
					position: absolute;
					right: 10rpx;
					top: -10rpx;
					background-color: red;
					color: white;
					padding-left: 14rpx;
					padding-right: 14rpx;
					border-radius: 60rpx;
					padding-top: 2rpx;
					padding-bottom: 2rpx;
					font-size: 24rpx;
				}

				.item_cover {
					width: 120rpx;
					height: 120rpx;
					border-radius: 40rpx;
					margin-right: 20rpx;
				}

				.item_content {
					flex: auto;
					display: flex;
					flex-direction: column;
					justify-content: space-around;

					.item_title {
						display: flex;
						justify-content: space-between;
						font-size: 36rpx;
						font-weight: 700;

						.time {
							font-size: 28rpx;
							font-weight: 400;
							color: $uni-text-color-placeholder;
						}
					}
				}
			}
		}

	}
</style>
