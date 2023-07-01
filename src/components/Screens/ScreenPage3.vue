<template>
  <div class="full-screen background-color-dark" v-on:mousewheel="mouseMove">

  </div>
</template>

<script>
import {defineComponent} from 'vue'
import * as d3 from "d3";
import {colorDark3, colorLight1, colorLight3} from "@/utils/globe";
import _ from "lodash";
import { legendColor } from 'd3-svg-legend'

export default defineComponent({
  name: "ScreenPage3",
  props:{
    data:[]
  },
  methods:{
    mouseMove(){
      this.initCurveChart()
    },
    initCurveChart(){
      let that=this
      function parliamentLayout(startAngle, endAngle, totalAngle, r0, r1, size) {
        // console.log(rowsCount)
        let points = [];
        let r = r0;
        let sum=0
        // console.log(this.jsonData)
        while (sum<that.data.length){
          let totalRingSeatsNumber = Math.round((totalAngle * r) / size);
          let newSize = (totalAngle * r) / totalRingSeatsNumber;
          sum+=totalRingSeatsNumber
          for (
              let k = Math.floor((startAngle * r) / newSize) * newSize;
              k < Math.floor((endAngle * r) / newSize) * newSize - 1e-6;
              k += newSize
          ) {
            let angle = k / r;
            let x = Math.cos(angle) * r;
            let y = Math.sin(angle) * r;
            points.push([x, y]);
          }
          r += size;
        }
        // console.log(points)
        return points;
      }
      const points=parliamentLayout(-Math.PI,Math.PI,Math.PI * 2,60,200,14)
      const svg = d3.select('#screen2-chart')
      const allCircle=svg.selectAll('circle')
      const orderedData=_.orderBy(this.data,['Party'],['desc'])
      allCircle.data(orderedData)
          .transition()
          .duration(1000)
          .attr('cx', function (d,key) {
            return points[key][0]+200
          })
          .attr('cy', function (d, key) {
            return points[key][1]+200
          })
          .attr('fill',function(d){
            switch (d['Party']) {
              case 'R':
                return colorDark3
              case 'D':
                return colorLight1
              case 'I':
                return colorLight3
              default:
                return 'white'
            }
          })
          .attr('r', 5)
    },
    initCurveChartLegend(){
      const labelList=["Democratic Party", "Republican Party", "No Party Affiliation", "Unknown"]
      const colorList=[ colorLight1, colorDark3, colorLight3, "white"]
      var ordinal = d3.scaleOrdinal()
          .domain(labelList)
          .range(colorList);

      var svg = d3.select("#screen3-chart");

      svg.append("g")
          .attr("class", "legendOrdinal")
          .attr("transform", "translate(500,20)");

      var legendOrdinal = legendColor()
          //d3 symbol creates a path-string, for example
          //"M0,-8.059274488676564L9.306048591020996,
          //8.059274488676564 -9.306048591020996,8.059274488676564Z"
          .shape("path", d3.symbol().type(d3.symbolCircle).size(120)())
          .shapePadding(10)
          //use cellFilter to hide the "e" cell
          .scale(ordinal);

      svg.select(".legendOrdinal")
          .call(legendOrdinal);

      svg.selectAll(".label")
          .attr('fill',function (d) {
            return colorList[_.indexOf(labelList,d)]
          })
          .attr('font-weight', 800)

    },
    getOffsetX(i,blockRowNum, offset){
      const blockIndex = _.floor(i / 25)
      const blockRow = blockIndex % blockRowNum
      const rowIndex = i % 25 % 5
      return 5 + blockRow * (12*5+6) + rowIndex * (5*2+2) + offset
    },
    getOffsetY(i,blockRowNum, offset){
      const blockIndex = _.floor(i / 25)
      const blockLine = _.floor(blockIndex / blockRowNum)
      const lineIndex = _.floor(i % 25 / 5)
      return 5+blockLine * (12*5+6) + lineIndex * (5*2+2) + offset
    },
    initChart1(){
      const svg = d3.select('#screen2-chart')
      let that=this
      const circleAppend = svg.selectAll('circle').data(this.data).enter().append("circle")
      circleAppend.attr('r', 5)
          .attr('fill', colorLight1)
          .attr('cx', function (d, i) {
            return that.getOffsetX(i, 10,0)
          })
          .attr('cy', function (d, i) {
            return that.getOffsetY(i,10, 0)
          })
    }
  },
  mounted() {
    this.initChart1()
  }
})
</script>

<style scoped lang="less">
@import "@/style/global.less";

</style>