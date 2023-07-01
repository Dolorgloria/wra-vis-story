<template>
  <div class="full-screen background-color-dark">
    <GraphChart></GraphChart>
  </div>
</template>

<script>
import {defineComponent} from 'vue'
import GraphChart from "@/components/Chart/GraphChart.vue";

export default defineComponent({
  name: "ScreenPage4",
  components: {GraphChart}
})
</script>

<style scoped lang="less">
@import "@/style/global.less";

</style>