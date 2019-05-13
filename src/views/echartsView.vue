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
      <p>武侯区地图 --- 用成都地图的json其余区域，剩下的武侯区的地图</p>
      <whMap></whMap>
    </div>
    <div class="mapDiv">
      <p>
        好的数据源推荐：<br/>
        1.<br/>
        项目：https://github.com/TangSY/echarts-map-demo <br/>
        在线体验：https://hxkj.vip/demo/echartsMap/  <br/>
        2.<br/>
        在线体验：http://datav.aliyun.com/tools/atlas/#&lat=33.521903996156105&lng=104.29849999999999&zoom=4  <br/>
        3.<br/>
        json数据：https://github.com/zhangqian00/echarts3-mapFile  <br/>
        4.<br/>
        自定义数据以及自定义数据获取：https://www.jianshu.com/p/7337c2f56876  <br/>
      </p>
    </div>
    <div class="mapfullDiv">
      <p>互动切换地图</p>
      <switchingMap></switchingMap>
    </div>
  </div>
</template>

<script>
    import '../assets/css/echartsView.css'
    import worldMap from '../components/echarts/worldMap'
    import chinaMap from '../components/echarts/chinaMap'
    import sichuanMap from '../components/echarts/sichuanMap'
    import cdMap from '../components/echarts/cdMap'
    import whMap from '../components/echarts/whMap'
    import switchingMap from '../components/echarts/switchingMap'
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
        cdMap,
        whMap,
        switchingMap
      }
    }
</script>

<style>

</style>
