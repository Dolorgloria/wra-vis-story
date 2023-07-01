<template>
  <div class="background-color-dark full-screen">
    <div id="screen1-str">
      {{screen1Str}}
    </div>
  </div>
</template>

<script>
import {defineComponent} from 'vue'

export default defineComponent({
  name: "ScreenPage1",
  data(){
    return{
      screen1Str: '\\ WHO RUNS AMERICA \\'
    }
  }
})
</script>

<style scoped lang="less">
@import "@/style/global.less";
#screen1-str{
  text-align: center;
  font-weight: bolder;
  color: #fff455;
  font-size: 80px;
  position: relative;
  top:50%;
  transform:translateY(-50%);
}
</style>