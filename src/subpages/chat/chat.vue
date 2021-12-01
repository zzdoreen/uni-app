<template>
	<view class="content">

		<!-- 聊天列表 -->
		<view class="list">
			<view class="left">
				<image class="avatar" src="../../static/logo.png" mode="widthFix"></image>
				<view class="text">
					<text>正在输入...</text>
				</view>
			</view>
			<view class="right">
				<view class="text">
					<text>正在输入...</text>
				</view>
				<image class="avatar" src="../../static/logo.png" mode="widthFix"></image>

			</view>
			<view class="left">
				<image class="avatar" src="../../static/logo.png" mode="widthFix"></image>
				<view class="text">
					<text>正在输入...</text>
				</view>
			</view>
			<view class="right">
				<view class="text">
					<text>正在输入...</text>
				</view>
				<image class="avatar" src="../../static/logo.png" mode="widthFix"></image>

			</view>
			<view class="left">
				<image class="avatar" src="../../static/logo.png" mode="widthFix"></image>
				<view class="text">
					<text>正在输入...</text>
				</view>
			</view>
			<view class="right">
				<view class="text">
					<text>正在输入...</text>
				</view>
				<image class="avatar" src="../../static/logo.png" mode="widthFix"></image>

			</view>
		</view>
		<!-- 聊天输入 -->
		<view class="bottom">
			<input class="input_text" type='text' placeholder="请输入内容" />
			<!-- <uni-icons type=""></uni-icons> -->
			<button size="small">发送</button>
		</view>

	</view>

</template>

<script>
</script>

<style>
	.content {
		background-color: #C0C0C0;
		width: 100vw;
		height: 100vh;
		overflow: hidden;
	}

	.list {
		border: 1px solid black;
		width: 100%;
		height: calc(100% - 40rpx);
		padding: 30rpx 10rpx 10rpx 10rpx;
		box-sizing: content-box;
		display: flex;
		flex-direction: column;
	}

	.left,
	.right {
		display: flex;
	}

	.right {
		align-self: flex-end;
	}

	.avatar {
		width: 80rpx;
		height: 80rpx;
		border-radius: 50%;
		border: 2px solid #F1F1F1;
		margin: 0 10rpx 0rpx 10rpx;
	}

	.text {
		background: white;
		font-size: 12px;
		height: 60rpx;
		border-radius: 10px;
		line-height: 60rpx;
		padding: 5px;
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
		width: 70%;
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
		background-color: #ccc;
		color: white;

	}
</style>
