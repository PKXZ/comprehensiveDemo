<template>
  <div class="mapContent">
    <div class="mapDiv">
      <p>世界地图</p>
      <worldMap></worldMap>
    </div>
    <div class="mapDiv">
      <p>中国地图</p>
      <!--<chinaMap></chinaMap>-->
    </div>
    <div class="mapDiv">
      <p>成都地图</p>
    </div>
    <div class="mapDiv">
      <p>宜宾地图</p>
    </div>
  </div>
</template>

<script>
    import '../assets/css/echartsView.css'
    import worldMap from '../components/echarts/worldMap'
    import chinaMap from '../components/echarts/chinaMap'
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
        chinaMap
      }
    }
</script>

<style>

</style>
