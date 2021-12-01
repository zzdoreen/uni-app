<script>
export default {
  onLaunch: function () {
    console.log("App Launch");
  },
  onShow: function () {
    console.log("App Show");
  },
  onHide: function () {
    console.log("App Hide");
  },
  onPageNotFound: function () {
    // console.log('404...')
    uni.navigateTo({
      url: "/page/404/index",
    });
  },
};
</script>

<style>
/*每个页面公共css */
</style>
