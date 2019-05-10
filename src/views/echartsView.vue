<template>
  <div class="mapContent">
    <div class="mapDiv">
      <p>世界地图</p>
      <worldMap></worldMap>
    </div>
    <div class="mapDiv">
      <p>中国地图</p>
      <chinaMap></chinaMap>
    </div>
    <div class="mapDiv">
      <p>四川省地图</p>
      <sichuanMap></sichuanMap>
    </div>
    <div class="mapDiv">
      <p>成都市地图</p>
      <cdMap></cdMap>
    </div>
    <div class="mapDiv">
      <p>武侯区地图</p>
    </div>
    <div class="mapDiv">
      <p>互动切换地图</p>
    </div>
  </div>
</template>

<script>
    import '../assets/css/echartsView.css'
    import worldMap from '../components/echarts/worldMap'
    import chinaMap from '../components/echarts/chinaMap'
    import sichuanMap from '../components/echarts/sichuanMap'
    import cdMap from '../components/echarts/cdMap'
    export default {
      name: "echartsView",
      data(){
          return{

          }
      },
      mounted() {
      },
      methods:{

      },
      components:{
        worldMap,
        chinaMap,
        sichuanMap,
        cdMap
      }
    }
</script>

<style>

</style>
