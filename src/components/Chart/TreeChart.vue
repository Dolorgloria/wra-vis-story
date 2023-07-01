<template>
  <div id="chart-container-6"></div>
</template>

<script>
import {defineComponent} from 'vue'
import * as echarts from "echarts";

export default defineComponent({
  name: "TreeChart",
  mounted() {
    this.initChart()
  },
  methods:{
    initChart(){
      console.log({children: [
        {
          name: 'Not Spanish or Latin White Ratio',
          value: Math.log(0.961064829*10000)
        },
        {
          name: 'Black and African ratio',
          value: Math.log(0.013397249*10000)
        },
        {
          name: 'American in ratio ',
          value: Math.log(0.002563414*10000)
        },
        {
          name: 'Some other race along ratio ',
          value: Math.log(0.000226902*10000)
        }
      ]})
      let myChart = echarts.init(document.getElementById('chart-container-6'), 'roma');
      const treemapOption = {
        series: [
          {
            type: 'treemap',
            id: 'echarts-package-size',
            animationDurationUpdate: 1000,
            roam: false,
            nodeClick: undefined,
            data: [
              {
                name: 'nodeA',
                value: 10,
                children: [
                  {
                    name: 'Not Spanish or Latin White Ratio',
                    value: 0.961064829*10000
                  },
                  {
                    name: 'Black and African ratio',
                    value: 0.013397249*10000
                  },
                  {
                    name: 'American in ratio ',
                    value: 0.002563414
                  },
                  {
                    name: 'Some other race along ratio ',
                    value: 0.000226902
                  }
                ]
              }],
            universalTransition: true,
            label: {
              show: true
            },
            breadcrumb: {
              show: false
            }
          }
        ]
      };
      myChart.setOption(treemapOption)
    }
  }
})
</script>

<style scoped lang="less">
#chart-container-6{
  width: 80%;
  margin-left: 10%;
  height: 100%;
}
</style>