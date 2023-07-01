<template>
    <div id="chart-container-5"></div>
</template>

<script>
import {defineComponent} from 'vue'
import * as echarts from "echarts";

export default defineComponent({
  name: "BarChart",
  mounted() {
    this.initChart()
  },
  methods: {
    initChart(){
      let myChart = echarts.init(document.getElementById('chart-container-5'), 'roma');
      let option = {
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          show:false
        },
        xAxis: [
          {
            type: 'value',
            min: 0,
            max: 2,
            interval: 0.5,
            splitLine:{
              show:false
            },
            alignTicks: true
          }
        ],
        yAxis: [
          {
            type: 'value',
            name: '对华激进程度',
            min: 0,
            max: 40,
            interval: 20,
            splitLine:{
              show:false
            },
            axisLabel: {
              formatter: '{value} %'
            }
          }
        ],
        series: [
          {
            name: '对华激进程度',
            type: 'bar',
            data: [
              [0.25, 3],
              [0.5, 12],
              [0.75, 21],
              [1, 23],
              [1.25, 18],
              [1.5, 26],
              [1.75, 33],
              [2, 9]
            ]
          }
        ]
      };
      myChart.setOption(option);
    }
  }
})
</script>

<style scoped lang="less">
@import "@/style/global.less";
#chart-container-5{
  width: 80%;
  margin-left: 10%;
  height: 100%;
}
</style>