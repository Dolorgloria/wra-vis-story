<template>
  <div id="map-container" class="background-color-dark"></div>
  <div id="bar-container" class="background-color-dark"></div>
</template>

<script>
import {defineComponent} from 'vue'
import data from '@/static/USA.json'
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'
import * as echarts from "echarts";

export default defineComponent({
  name: "MapChart",
  mounted() {
    let map = L.map('map-container', {
      center: [38.633, -78.283-20],
      zoom: 4,
      attributionControl: false,
      zoomControl:false
    })
    L.geoJSON(data).addTo(map);
    this.initBarCart()
  },
  methods:{
    initBarCart(){
      const sizeValue='57%'
      let myCart=echarts.init(document.getElementById('bar-container'))
      let option = {
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'shadow'
          }
        },
        legend: {
          show:false
        },
        grid:  [
          { right: sizeValue, bottom: sizeValue },
          { left: sizeValue, bottom: sizeValue },
          { right: sizeValue, top: sizeValue },
        ],
        xAxis: [
          {
          type: 'value',
          gridIndex:0,
          axisLabel:{
            color:'white',
            fontWeight: 'bold'
          },
            interval:100000
        }, {
          type: 'value',
          gridIndex:1,
          axisLabel:{
            color:'white',
            fontWeight: 'bold'
          }
        }, {
          type: 'value',
          gridIndex:2,
          axisLabel:{
            color:'white',
            fontWeight: 'bold'
          },
            splitLine:{
            lineStyle: {
              color: 'white',
              width: 2
            }
            },
            name:'比例',
            nameTextStyle:{color:'white', fontWeight:'bold'}
        }],
        yAxis: [{
          type: 'category',
          data: ['加州20选区', '加州37选区', '纽约州'],
          gridIndex: 0,
          axisLabel:{
            color:'white',
            fontWeight: 'bold'
          }
        },{
          type: 'category',
          data: ['加州20选区', '加州37选区', '纽约州'],
          gridIndex: 1,
          axisLabel:{
            color:'white',
            fontWeight: 'bold'
          }
        }, {
          type: 'category',
          data: ['加州20选区', '加州37选区', '纽约州'],
          gridIndex: 2,
          axisLabel:{
            color:'white',
            fontWeight: 'bold'
          }
        }],
        series: [
          {
            name: '贫困人口比例',
            type: 'bar',
            data: [0.115, 0.185, 0.159],
            xAxisIndex:0,
            yAxisIndex:0
          },
          {
            name: '人均年收入',
            type: 'bar',
            data: [19325, 23438, 31000],
            xAxisIndex:0,
            yAxisIndex:0
          },
          {
            name: '家庭收入中位数',
            type: 'bar',
            data: [297598,254061,71919],
            xAxisIndex:0,
            yAxisIndex:0
          },
          {
            name: '高中学历人口比例',
            type: 'bar',
            data: [0.759, 0.813, 0.883],
            xAxisIndex:1,
            yAxisIndex:1
          },
          {
            name: '本科学历人口比例',
            type: 'bar',
            data: [0.28, 0.39, 0],
            xAxisIndex:1,
            yAxisIndex:1
          },
          {
            name: '城市人口比例',
            type: 'bar',
            data: [31,76.9,45.2],
            xAxisIndex:2,
            yAxisIndex:2
          },
          {
            name: '郊区人口比例',
            type: 'bar',
            data: [53.5,22.6,41.5],
            xAxisIndex:2,
            yAxisIndex:2
          },
          {
            name: '农村人口比例',
            type: 'bar',
            data: [15.5,0.5,13.3],
            xAxisIndex:2,
            yAxisIndex:2
          }
        ]
      };
      myCart.setOption(option)
    }
  }
})
</script>

<style scoped lang="less">
#map-container {
  width:40%;
  height:43vh;
  position: absolute;
  left: 47%;
  top:47%;
  background-color: rgb(14,14,14);
}
#bar-container{
  width: 80%;
  height:100vh;
}
</style>