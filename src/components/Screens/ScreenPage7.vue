<script>
import {defineComponent} from 'vue'
import TreeChart from "@/components/Chart/TreeChart.vue";

export default defineComponent({
  name: "ScreenPage7",
  components: {TreeChart}
})
</script>

<template>
  <div class="background-color-dark full-screen">
    <TreeChart></TreeChart>
  </div>
</template>

<style scoped lang="less">
@import "@/style/global.less";
</style>