<template>
  <div id="graph-chart"></div>
</template>

<script>
import {defineComponent} from 'vue'
import * as echarts from 'echarts';
import data from '@/static/congress.json'
import _ from "lodash";

export default defineComponent({
  name: "GraphChart",
  data(){
    return{
      data:data,
      categoties:[
        {
          "name": "参议院 - 共和党"
        },
        {
          "name": "众议院 - 共和党"
        },
        {
          "name": "参议院 - 民主党"
        },
        {
          "name": "众议院 - 共和党"
        },
        {
          "name": "其他"
        }]
    }
  },
  mounted() {
    this.initChart()
  },
  methods:{
    initChart(){
      console.log(_.orderBy(this.data,['PageRank_total'],['desc']))

      let myEchart=echarts.init(document.getElementById('graph-chart'))
      let option = {
        tooltip: {},
        legend:{
          textStyle:{
            color: 'white'
          }
        },
        animationDurationUpdate: 1500,
        animationEasingUpdate: 'quinticInOut',
        series: [
          {
            type: 'graph',
            layout: 'circular',
            circular: {
              rotateLabel: true
            },
            data: this.data.nodes,
            links: this.data.links,
            categories:this.categoties,
            roam: true,
            label: {
              position: 'right',
              formatter: '{b}'
            },
            lineStyle: {
              color: 'source',
              curveness: 0.3
            }
          }
        ]
      };
      myEchart.setOption(option)
    }
  }
})
</script>

<style scoped lang="less">
@import "@/style/global.less";
#graph-chart{
  width: 80%;
  margin-left: 10%;
  height: 500px;
}
</style>