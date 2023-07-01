<template>
  <AllPages></AllPages>
<!--  <ScreenPage8></ScreenPage8>-->
  <div style="height: 100%;background: url(@/static/img/overlay.png);"></div>
</template>

<script>
import AllPages from "@/components/AllPages.vue";
// import ScreenPage8 from "@/components/Screens/ScreenPage8.vue";

export default {
  name: 'App',
  components: {
    // ScreenPage8,
    AllPages,
  }
}
</script>

<style lang="less">

</style>
