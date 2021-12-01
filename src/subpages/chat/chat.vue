<template>
	<view class="content">

		<!-- 聊天列表 -->
		<view class="list">
			<view :class="item.isMe?'right':'left'" v-for="(item,key) in chatList" :key='key'>
				<image v-if="!item.isMe" class="avatar" src="../../static/logo.png" mode="widthFix"></image>
				<view :class="item.type==='text'?'text':'image_info'">
					<text v-if="item.type==='text'">{{item.content}}</text>
					<image v-else :src="item.content"></image>
				</view>
				<image v-if="item.isMe" class="avatar" src="../../static/logo.png" mode="widthFix"></image>
			</view>
		</view>

		<!-- 聊天输入 -->
		<view class="bottom">
			<input class="input_text" type='text' placeholder="请输入内容" v-model="content" />
			<image class="bottom_image" mode="widthFix" @click="handleChooseImage"
				src="https://img0.baidu.com/it/u=2862203040,3186546841&fm=26&fmt=auto">
			</image>
			<button size="small" @click="handleSend">发送</button>
		</view>

	</view>

</template>

<script>
	export default {
		data() {
			return {
				content: '',
				chatList: [{
						isMe: false,
						type: 'text',
						content: 'aaa'
					},
					{
						isMe: true,
						type: 'image',
						content: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201705%2F16%2F20170516135450_vsUG2.jpeg&refer=http%3A%2F%2Fb-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1640937609&t=83493b8e2a3460f6ba6de209749cb1a0'
					},
					{
						isMe: false,
						type: 'text',
						content: 'bbb'
					},
					{
						isMe: true,
						type: 'text',
						content: 'bbb'
					},
					{
						isMe: true,
						type: 'text',
						content: 'bbb'
					},
				]
			}
		},
		onShow() {
			if (uni.getStorageSync('data')) {
				this.chatList = JSON.parse(uni.getStorageSync('data'))
			}
			setTimeout(() => {
				uni.pageScrollTo({
					scrollTop: 9999999999999999999999,
					duration: 0
				})
			}, 10)

		},
		methods: {
			handleChooseImage() {
				uni.chooseImage({
					count: 1,
					sizeType: ['original', 'compressed'],
					sourceType: ['album', 'camera'],
					success: (res) => {

						this.chatList.push({
							isMe: true,
							type: 'image',
							content: res.tempFiles[0].path
						})
						uni.setStorageSync('data', JSON.stringify(this.chatList))
						setTimeout(() => {
							uni.pageScrollTo({
								scrollTop: 9999999999999999999999,
								duration: 0
							})
						}, 10)

					}
				})
			},
			handleSend() {
				this.chatList.push({
					isMe: true,
					type: 'text',
					content: this.content
				})
				this.content = ''
				uni.setStorageSync('data', JSON.stringify(this.chatList))
				setTimeout(() => {
					uni.pageScrollTo({
						scrollTop: 9999999999999999999999,
						duration: 0
					})
				}, 10)
			}
		}
	}
</script>

<style>
	.content {
		background-color: #EBEBEB;
		height: auto;
		overflow: scroll;
	}

	.list {
		width: 100%;
		height: auto;
		padding: 30rpx 10rpx 10rpx 10rpx;
		box-sizing: content-box;
		display: flex;
		flex-direction: column;
		margin-bottom: 100px;
	}

	.left,
	.right {
		display: flex;
		position: relative;
	}

	.right {
		align-self: flex-end;
	}

	.avatar {
		width: 80rpx;
		height: 80rpx;
		border-radius: 50%;
		border: 2px solid #F1F1F1;
		margin: 0 10rpx 0rpx 5rpx;
	}

	.text {
		background: white;
		font-size: 12px;
		height: 60rpx;
		border-radius: 10px;
		line-height: 60rpx;
		padding: 3px 15px;
		margin: 10px 10px 0 10px;
	}

	.image_info {
		background: white;
		font-size: 12px;
		border-radius: 10px;
		line-height: 60rpx;
		padding: 3px 10px;
		margin: 10px 10px 0 10px;

	}

	.right .image_info {
		background-color: #ABD33D;
	}

	.image_info image {
		max-width: 200px;
	}


	.left .text::after,
	.left .image_info::after {
		content: '';
		display: inline-block;
		position: absolute;
		left: 105rpx;
		border: 10px solid white;
		border-bottom-color: transparent;
		border-left-color: transparent
	}


	.right .text::after,
	.right .image_info::after {
		content: '';
		display: inline-block;
		position: absolute;
		right: 90rpx;
		border: 10px solid #ABD33D;
		border-bottom-color: transparent;
		border-right-color: transparent
	}

	.right .text {
		background: #ABD33D;
		color: white;
	}

	.bottom {
		position: fixed;
		bottom: 0;
		background: white;
		width: 100%;
		height: 45px;
		/* border: 1px solid #007AFF; */
		display: flex;
		padding-top: 10px;
		padding-left: 5px;
		flex-direction: row;
		border-radius: 5px;
	}

	.input_text {
		width: 60%;
		font-size: 12px;
		border: 1px solid #C0C0C0;
		border-radius: 5px;
		height: 70rpx;

		padding-left: 5px;
	}

	.bottom button {
		width: 150rpx;
		font-size: 12px;
		height: 70rpx;
		background-color: #ABD33D;
		color: white;

	}

	.bottom_image {
		width: 50rpx;
		hieght: 50rpx;
		margin: 5px 5px 0 10px;
	}
</style>
