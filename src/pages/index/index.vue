<template>
	<view class="content">
		<!-- <image class="logo" src="/static/logo.png"></image> -->
		<child :msg='title' @getChild='say'></child>
		
		<br>
		<view>
			<!-- <text class="title">{{ title }}</text> -->
			<navigator url="../../subpages/chat/chat">聊天室</navigator>
		</view>
		<!-- <navigator open-type="switchTab" url="/pages/me/index">me</navigator> -->
	</view>
</template>

<script>
	import Child from '@/componets/child.vue'
	export default {
		data() {
			return {
				title: "Hello",
			};
		},
		components:{
			Child
		},
		onLoad() {
			console.log("load");
		},
		onShow() {
			console.log("show");
		},
		methods: {
			say(info){
			
			this.title =info
			}
		},
	};
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin: 200rpx auto 50rpx auto;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
