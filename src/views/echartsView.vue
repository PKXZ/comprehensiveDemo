<template>
  <div>
    <div id="myChart" style="width:100%; height: 800px;border:1px solid #000;"></div>
  </div>
</template>

<script>
  import china from 'echarts/map/json/china.json'
    export default {
      name: "echartsView",
      data(){
          return{

          }
      },
      mounted() {
        this.drawLine();
      },
      methods:{
        drawLine(){
          // 基于准备好的dom，初始化echarts实例
          var imgjing = "/public/img/jing.png";
          var myChartContainer = document.getElementById('myChart');
          var myChart = this.$echarts.init(myChartContainer);
          this.$echarts.registerMap('china', china);
          // 绘制图表
          var optionMap = {
            backgroundColor: "#000617",//地图背景颜色
            //提示框组件
            tooltip: {
              show: true,
              enterable: true,//鼠标是否可进入提示框浮层中，默认为false
              padding: [0 ,20],
              hideDelay: 0,//浮层隐藏的延迟，单位为ms
              textStyle: { //提示框浮层的文本样式
                fontSize: 14 //文字的字体大小默认14
              }
            },
            //地理坐标系组件 -- 这个是重点配置区
            geo: {
              map: 'china', // 表示中国地图
              roam: true,//是否开启鼠标缩放和平移漫游
              aspectScale: 1, //地图的长宽比
              zoom: 1.2,//当前视角的缩放比例
              //图形上的文本标签
              label: {
                show: true, // 是否显示对应地名
                textStyle: {
                  color: '#ffffff'//地名字体颜色
                }
              },
              //地图区域的多边形 图形样式
              itemStyle: {
                areaColor: 'transparent',//模块内的颜色
                borderColor: '#b7d25c',//模块边框的颜色
                borderWidth: 1
              },
              //高亮状态下的多边形和标签样式
              emphasis: {
                itemStyle: {
                  areaColor: '#1890ff',//移动上去的模块颜色
                  borderColor: '#b7d25c',//移动上去的模块边框颜色
                  borderWidth: 1,
                }
              }
            },
            //系列列表
            series: [
              {
                name: '启动次数', //浮动框的标题
                symbol: 'image:/' + imgjing,
                type: 'map', //地图主要用于地理区域数据的可视化
                geoIndex: 0,//默认情况下，map series 会自己生成内部专用的 geo 组件。但是也可以用这个 geoIndex 指定一个 geo 组件。这样的话，map 和 其他 series（例如散点图）就可以共享一个 geo 组件了。并且，geo 组件的颜色也可以被这个 map series 控制，从而用 visualMap 来更改
                data: [{
                  "name": "北京",
                  "value": 599
                }, {
                  "name": "上海",
                  "value": 142
                }, {
                  "name": "黑龙江",
                  "value": 44
                }, {
                  "name": "深圳",
                  "value": 92
                }, {
                  "name": "湖北",
                  "value": 810
                }, {
                  "name": "四川",
                  "value": 453
                }]
              }
            ]
          }

          myChart.setOption(optionMap);
          window.onresize=function(){
            myChart.resize();
          }

        }
      }
    }
</script>

<style>

</style>
