<template>

  <div class="component">
    <div class="overlay"></div>
    <div class="item">
      <img src="../../static/img/screen6/img1.png" class="item-img">
      美国
    </div>
    <div class="item">
      <img src="../../static/img/screen6/img2.png" class="item-img">
      国会
    </div>
    <div class="item">
      <img src="../../static/img/screen6/img3.png" class="item-img">
      重点议员
    </div>
    <div class="item">
      <img src="../../static/img/screen6/img4.png" class="item-img">
      决策结构
    </div>
    <div class="item">
      <img src="../../static/img/screen6/img5.png" class="item-img">
      法案
    </div>

    <v-btn @click="translateOverlay">
      动画
    </v-btn>
  </div>
</template>

<script>
import {defineComponent} from 'vue'
import anime from "animejs";

export default defineComponent({
  name: "FlowChart",
  methods:{
    translateOverlay(){
      console.log(123)
      anime({
        targets: '.overlay',
        keyframes: [
          {translateX: 100},
          {translateX: 200},
          {translateX: 300},
          {translateX: 400},
          {translateX: 0}
        ],
        duration: 4000,
        loop: false,
        easing: 'easeInOutExpo'
      });
    }
  }
})
</script>

<style scoped lang="less">
@import "@/style/global.less";
.component{
  //text-align: center;
  transform: translate(25%, 50%);
}
.item{
  margin-top: 10px;
  color:@color-light-1 ;
  font-weight: bold;
  width: 100px;
  display: inline-block;
  text-align: center;
}
.overlay{
  width: 100px;
  height: 130px;
  background-color: #fef47150;
  border: #fece00 2px solid;
  z-index: 3;
  position: absolute;
  bottom:0;
}
img{
  height: 80px;
  width: 80px;
}
</style>