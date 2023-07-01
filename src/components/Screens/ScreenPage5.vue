<script>
import {defineComponent} from 'vue'
import BarChart from "@/components/Chart/BarChart.vue";

export default defineComponent({
  name: "ScreenPage5",
  components: {BarChart}
})
</script>

<template>
  <div class="full-screen background-color-dark">
    <BarChart></BarChart>
  </div>

</template>

<style scoped lang="less">
@import "@/style/global.less";

</style>