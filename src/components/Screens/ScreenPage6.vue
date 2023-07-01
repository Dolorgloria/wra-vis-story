<script>
import {defineComponent} from 'vue'
import FlowChart from "@/components/Chart/FlowChart.vue";

export default defineComponent({
  name: "ScreenPage6",
  components: {FlowChart}
})
</script>

<template>
  <div class="background-color-dark full-screen">
    <FlowChart></FlowChart>
  </div>
</template>

<style scoped lang="less">
@import "@/style/global.less";
</style>