<template>
	<view>
		<text>子组件</text>
		{{msg}}
		<button type="default" @click="getChild">子传父</button>
	</view>
</template>

<script>
	export default {
		props:['msg'],
		data() {
			return {}
		},
		methods: {
			getChild(){
				this.$emit('getChild','aaaa')
				uni.$emit('getMeFun','a-me')
			}
		}
	}
</script>

<style scoped>
text{
	color:red
}
</style>
