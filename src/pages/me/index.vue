<template>
  <view>
    <text>{{name}}</text>
  </view>
</template>
<script>
export default {
  data() {
    return {
		name:'me'
	};
  },
  onLoad() {
	  uni.$on('getMeFun',(str)=>{
		  this.name = str
		  console.log('me 页面的全局事件被触发')
	  })
    // let timmer = setTimeout(() => {
    //   clearInterval(timmer);
    //   uni.navigateTo({ url: "pages/index/index" });
    // }, 2000);
  },
  methods: {
  },
};
</script>