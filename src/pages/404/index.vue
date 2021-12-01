<template>
  <view>
    <text>页面不存在!!</text>
  </view>
</template>
<script>
export default {
  data() {
    return {};
  },
  onLoad() {
    // #ifdef H5
    
    // #endif
    let timmer = setTimeout(() => {
      clearInterval(timmer);
      uni.navigateTo({ url: "/pages/index/index" });
    }, 2000);
  },
  methods: {
  },
};
</script>