<template>
  <div>
    <full-page ref="fullpage" :options="options" id="fullpage">
      <div v-if="false" class="section">
        <div id="screen1-str">
          {{'\\Who Runs America\\'}}
        </div>
      </div>
      <div class="section">
        <UnitChart :data="data"></UnitChart>
      </div>
      <div v-if="false" class="section">
        <MapChart></MapChart>
      </div>
      <div class="section">
        <GraphChart></GraphChart>
      </div>
      <div class="section">
        <LineChart></LineChart>
      </div>
    </full-page>
  </div>
</template>

<script>
import data from '@/static/data.json'
import {colorBlack} from "@/utils/globe";
import UnitChart from "@/components/Chart/UnitChart.vue";
import MapChart from "@/components/Chart/MapChart.vue";
import GraphChart from "@/components/Chart/GraphChart.vue";
import LineChart from "@/components/Chart/LineChart.vue";
export default {
  name: 'AllPages',
  components: {
    LineChart,
    GraphChart,
    MapChart,
    UnitChart,
  },
  data(){
    return{
      data:data,
      options: {
        licenseKey: 'YOUR_KEY_HEERE',
        sectionsColor: [colorBlack, colorBlack,colorBlack,colorBlack]
      }
    }
  },
  mounted() {
    console.log(data)
  },
  methods:{
  }
}
</script>

<style scoped lang="less">
@import "@/style/global.less";
#screen1-str{
  text-align: center;
  font-weight: bolder;
  color: rgb(255, 69, 59);
  font-size: 80px;
  position: relative;
  top:50%;
  transform:translateY(-50%);
}
</style>