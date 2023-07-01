<template>
  <div class="background-color-dark full-screen">
    <MapChart></MapChart>
  </div>
</template>

<script>
import {defineComponent} from 'vue'
import MapChart from "@/components/Chart/MapChart.vue";

export default defineComponent({
  name: "ScreenPage2",
  components: {MapChart}
})
</script>

<style scoped lang="less">
@import "@/style/global.less";


</style>