<template>
  <!--四川地图-->
  <div id="sichuanChart" class="maps"></div>
</template>

<script>
  import sichuan from 'echarts/map/json/province/sichuan.json'
  export default {
    name: "sichuanMap",
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
        const sichuanChartContainer = document.getElementById('sichuanChart');
        const sichuanChart = this.$echarts.init(sichuanChartContainer);
        this.$echarts.registerMap('sichuan', sichuan);
        // 绘制图表
        const optionMap = {
          backgroundColor: 'rgba(0,51,102, 1)',//地图背景颜色
          //视觉映射组件
          visualMap: {
            show: false,
            inRange: {//定义在选中范围中的视觉元素
              color: ['#2f6dbc','#5a98df','#2b5a9b','#3a85dc'],
            }
          },
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
            map: 'sichuan', // 表示XX地图
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
              borderColor: '#00effc',//模块边框的颜色
              borderWidth: 1
            },
            //高亮状态下的多边形和标签样式
            emphasis: {
              itemStyle: {
                areaColor: '#1890ff',//移动上去的模块颜色
                borderColor: '#b7d25c',//移动上去的模块边框颜色
                borderWidth: 1
              },
              label: {
                show: true,
                color: '#b7d25c'//标签文字颜色
              }
            }
          },
          //系列列表
          series: [
            {//标记点样式
              type: 'scatter',
              coordinateSystem: 'geo',
              symbol: 'path://M370.758 476.69c0 52.966-35.31 194.206-123.586 194.206-52.966 0-105.932-52.966-88.276-123.586s88.276-141.242 141.242-141.242c39.002 0 70.62 31.62 70.62 70.622zM653.242 476.69c0 52.966 35.31 194.206 123.586 194.206 52.966 0 105.932-52.966 88.276-123.586-17.656-70.62-88.276-141.242-141.242-141.242-39.002 0-70.62 31.62-70.62 70.622zM683.38 693.724a17.65 17.65 0 0 0-24.966 0l-16.586 16.578c-7.828 7.81-19.034 11.55-29.966 10l-82.206-11.748v-47.32c2.018-0.718 4.092-1.212 6.032-2.18l28.88-14.44a32.656 32.656 0 0 0 18.054-29.212v-0.12c0-18.04-14.622-32.662-32.662-32.662h-75.918c-18.04 0-32.662 14.622-32.662 32.662v0.118a32.66 32.66 0 0 0 18.054 29.212l28.88 14.44c1.938 0.968 4.014 1.464 6.032 2.18v47.318l-82.19 11.74c-11.086 1.612-22.156-2.18-29.982-9.982l-16.588-16.586a17.65 17.65 0 0 0-24.966 0 17.65 17.65 0 0 0 0 24.966l16.588 16.596c15.656 15.63 38.138 23.112 59.93 19.966L512 741.698l94.878 13.562c3.276 0.466 6.57 0.69 9.844 0.69 18.586 0 36.776-7.388 50.07-20.672l16.588-16.586a17.65 17.65 0 0 0 0-24.968z',
              symbolSize: 30,//标记点大小
              symbolOffset: ['0', '-80%'],//标记点位置
              data: [{//标记点数据
                name: '我是成都市的经纬度',
                value: [104.06, 30.67]
              }
              ],
            },{
              name: '启动次数', //浮动框的标题
              type: 'map', //地图主要用于地理区域数据的可视化
              geoIndex: 0,//默认情况下，map series 会自己生成内部专用的 geo 组件。但是也可以用这个 geoIndex 指定一个 geo 组件。这样的话，map 和 其他 series（例如散点图）就可以共享一个 geo 组件了。并且，geo 组件的颜色也可以被这个 map series 控制，从而用 visualMap 来更改
              data: [{
                "name": "宜宾市",
                "value": 599
              }, {
                "name": "成都市",
                "value": 142
              }]
            }
          ]
        }
        //sichuanChart.showLoading();
        sichuanChart.setOption(optionMap,true);//是否不跟之前设置的 option 进行合并，默认为 false，即合并

        window.onresize=function(){
          sichuanChart.resize();
          //sichuanChart.hideLoading();
        }

      }
    }
  }
</script>

<style>

</style>
