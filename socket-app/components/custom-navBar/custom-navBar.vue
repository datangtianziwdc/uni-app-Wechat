<template>
	<view class="app_bar">
		<view class="size_box"></view>
		<view class="container">
			<image :class="left_icon_type==='icon'?'left_icon':'app_avatar'" :src="left_icon"
				@click="clickHandle('back')"></image>
			<image class="app_avatar" src="/static/images/logo.png" v-if="left_icon_type!=='icon'"></image>
			<view v-else>
				开心就好
			</view>
			<view class="actions" v-if="left_icon_type!=='icon'">
				<image class="actions_icon" src="/static/images/search.png" @click="clickHandle('search')"></image>
				<view style="width: 20rpx;"></view>
				<image class="actions_icon" src="/static/images/add.png"></image>
			</view>
			<template>
				<image class="app_avatar" :src="avatar" @click="clickHandle('search')"></image>
			</template>
		</view>
	</view>
</template>

<script>
	export default {
		name: "custom-navBar",
		props: {
			left_icon: {
				type: String,
				default: "/static/images/back.png"
			},
			left_icon_type: {
				type: String,
				default: "icon"
			},
			avatar: {
				type: String,
				default: ""
			}
		},
		data() {
			return {
				clickHandle(type) {
					switch (type) {
						case 'back':
							uni.navigateBack({
								delta: 1
							})
							break;
					}
				}
			};
		}
	}
</script>

<style lang="scss">
	.app_bar {
		padding-top: var(--status-bar-height);

		.size_box {
			height: 120rpx;
			width: 100%;
			background-color: yellow;
		}

		.container {
			// background-color: yellow;
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding-top: 10rpx;
			padding-bottom: 10rpx;
			padding-left: 20rpx;
			padding-right: 20rpx;
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

			.left_icon {
				width: 50rpx;
				height: 50rpx;
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

			.app_logo {
				display: flex;
				justify-content: center;
				flex: auto;
			}

			.actions {
				display: flex;
			}
		}
	}
</style>
