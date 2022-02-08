<template>
	<view class="chat_page">
		<custom-navBar :avatar="userInfo.avatar"></custom-navBar>
		<!-- 聊天列表 -->
		<view class="list_view">
			<view class="item_left" v-for="i in 10">
				<view>
					<image :src="userInfo.avatar" mode="" class="item_avatar"></image>
				</view>
				<view class="item_content">
					三个地方公司规定的是个帅哥沙发沙发斯蒂芬是的发送到三个地方公司规定的是个帅哥沙发沙发斯蒂芬是的发送到三个地方公司规定的是个帅哥沙发沙发斯蒂芬是的发送到
				</view>
			</view>
			<view class="item_right" v-for="i in 10">
				<view class="item_content">
					三个地方公司规定的是个帅哥沙发沙发斯蒂芬是的发送到三个地方公司规定的是个帅哥沙发沙发斯蒂芬是的发送到三个地方公司规定的是个帅哥沙发沙发斯蒂芬是的发送到
				</view>
				<view>
					<image :src="userInfo.avatar" mode="" class="item_avatar"></image>
				</view>
			</view>
		</view>
		<view class="app_bottom">
			<image src="/static/images/keyboard.png" mode="" class="bottom_icon" @click="clickHandle('switch')"
				v-show="isShow"></image>
			<image src="/static/images/audio.png" mode="" class="bottom_icon" @click="clickHandle('switch')"
				v-show="!isShow"></image>
			<!-- <u-input placeholder="请输入内容" :border="true" v-model="value" @change="change" :clearable="false"></u-input> -->
			<u-input
			    placeholder="请输入内容"
			    border="surround"
			    v-model="value"
				:confirmHold="true"
				confirmType="send"
				@confirm="clickHandle('send')"
			  ></u-input>
			<image src="/static/images/smile.png" mode="" class="bottom_icon"></image>
			<image src="/static/images/add-circle.png" mode="" class="bottom_icon"></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo: {
					avatar: "https://img2.baidu.com/it/u=1024596825,4008732728&fm=253&fmt=auto&app=138&f=JPEG?w=513&h=500"
				},
				isShow: false,
				value: "",
				autoHeight:true
			};
		},
		methods: {
			clickHandle(type,e) {
				switch (type) {
					case 'switch':
						this.isShow = !this.isShow;
						break;
					case 'send':
					uni.showModal({
						content: '提示',
						showCancel: false
					});
						break;
				}
			}
		}
	}
</script>

<style lang="scss">
	.chat_page {
		background-color: #F4F4F4;

		.list_view {
			padding-bottom: 150rpx;

			.item_left,
			.item_right {
				margin-bottom: 20rpx;
				display: flex;
				align-items: flex-start;
				padding-right: 140rpx;
				padding-left: 20rpx;

				.item_avatar {
					width: 100rpx;
					height: 100rpx;
					border-radius: 20rpx;
					margin-right: 20rpx;
				}

				.item_content {
					background-color: #ffffff;
					padding-left: 20rpx;
					padding-right: 20rpx;
					padding-top: 10rpx;
					padding-bottom: 10rpx;
					font-size: 30rpx;
					border-radius: 20rpx;
				}
			}

			.item_right {
				justify-content: flex-end;
				padding-right: 20rpx;
				padding-left: 140rpx;

				.item_avatar {
					margin-right: 0;
					margin-left: 20rpx;
				}

				.item_content {
					background-color: #00ff00;
				}
			}
		}

		.app_bottom {
			background-color: white;
			position: fixed;
			display: flex;
			bottom: 0;
			left: 0;
			right: 0;
			padding-bottom: 40rpx;
			padding-top: 20rpx;
			padding-left: 10rpx;
			padding-right: 10rpx;
			align-items: center;

			.bottom_icon {
				height: 80rpx;
				width: 80rpx;
				margin-left: 6rpx;
				margin-right: 6rpx;
			}
		}
	}
</style>
