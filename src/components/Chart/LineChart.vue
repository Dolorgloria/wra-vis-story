<script>
import {defineComponent} from 'vue'
import * as echarts from "echarts";
import data from '@/static/state.json'
import _ from "lodash";

export default defineComponent({
  name: "LineChart",
  mounted() {
    this.initChart()
  },
  methods:{
    initChart(){
      let dataList=[]
      _.forEach(data, function (item) {
        let tmp={
          name:item['State'],
          type: 'line',
          data:[item['2013年'],item['2014年'],item['2015年'],item['2016年'],item['2017年'],item['2018年'],item['2019年'],item['2020年'],item['2021年'],item['2022年']]
        }
        dataList.push(tmp)
        // console.log(tmp)
      })
      console.log(data[0])
      let myChart = echarts.init(document.getElementById('line-chart'));
      let option = {
        tooltip: {
          trigger: 'item'
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: {
          type: 'category',
          boundaryGap: true,
          axisLabel:{
            color:'white',
            fontWeight: 'bold'
          },
          data: ['2013年', '2014年', '2015年', '2016年', '2017年', '2018年', '2019年', '2020年','2021年','2022年']
        },
        yAxis: {
          type: 'value',
          axisLabel:{
            color:'white',
            fontWeight: 'bold'
          },
        },
        series:dataList
      };
      myChart.setOption(option)
    }
  }
})
</script>

<template>
  <div id="line-chart"></div>
</template>

<style scoped lang="less">
#line-chart{
  width: 80%;
  margin-left: 10%;
  height: 500px;
}
</style>