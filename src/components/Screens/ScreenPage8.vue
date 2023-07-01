<template>
  <div class="full-page">
    <div id="overlay"></div>
  </div>


<!--  <div class="background-color-dark">-->
<!--    <svg id="screen8-chart" style="position: absolute;top: 80px;left: 80px" width="1200" height="800"></svg>-->
<!--  </div>-->
</template>

<script>
import {defineComponent} from 'vue'
import data from '@/static/data.json'
import * as d3 from "d3";
import _ from "lodash";
import {colorBlue1, colorRed1} from "@/utils/globe";

export default defineComponent({
  name: "ScreenPage8",

  mounted() {
    this.initChart()
  },
  methods:{
    initChart(){
      const svg=d3.select('#screen8-chart')
      const circleAppend=svg.selectAll('circle').data(_.orderBy(data, ['Party2'], ['desc'])).enter().append('circle')
      circleAppend.attr('r', 5)
          .attr('fill', function (d) {
            if (_.isEqual(d['Party2'], 0)){
              return colorBlue1
            }else if (_.isEqual(d['Party2'], 1)){
              return colorRed1
            }else {
              return colorBlue1
            }
          })
          .attr('cx', function (d, i) {
            return (Math.floor((i/24))+1)*12
          })
          .attr('cy', function (d, i) {
            return ((i%24)+1)*12
          })
    }
  }
})
</script>

<style scoped lang="less">
@import "@/style/global.less";
#overlay{
  background: url(@/static/img/overlay.png);
  width: 100%;
  height: 100%;
}
.full-screen{
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
}
</style>