<template>
  <!--成都市地图-->
  <div id="cdChart" class="maps"></div>
</template>

<script>
  import cd from './cd.json'
  export default {
    name: "cdMap",
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
        const cdChartContainer = document.getElementById('cdChart');
        const cdChart = this.$echarts.init(cdChartContainer);
        this.$echarts.registerMap('cd', cd);
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
            map: 'cd', // 表示XX地图
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
              symbol: 'path://M687.1 551.3c48.2-46.8 46.8-129.1 52.2-164.8 7.2-47.4 63.1-28.1 107.9-73.8 18.8-19.1 44.8-97.3 24.4-97.3H619.4 618 365.8c-20.4 0 5.6 78.2 24.4 97.3 44.8 45.6 100.7 26.4 107.9 73.8 5.4 35.7 4 118 52.2 164.8 0 0 10.5 11.3 30.4 18.9h-3.6c2.3 10 5.7 72.1 5.7 102.7V871h-2.6s-96.7 29.5-118.1 35.7c-21.4 6.1-20.8 17.1-19 20.5 5.5 10 28.9 16.1 82.1 20.2 55.4 4.3 89.2 4.1 93 4.1 3.7 0 37.6 0.2 93-4.1 53.2-4.1 76.6-10.2 82.1-20.2 1.8-3.3 2.4-14.3-19-20.5-21.4-6.1-118.1-35.7-118.1-35.7h-2.6V672.9c0-30.7 3.3-92.8 5.7-102.7h-1.7c20.2-7.6 29.5-18.9 29.5-18.9z',
              symbolSize: 30,//标记点大小
              symbolOffset: ['0', '-80%'],//标记点位置
              data: [{//标记点数据
                name:'成都市武侯高级中学',
                value: [104.009429,30.60156]
              }
              ],
            },{
              name: '启动次数', //浮动框的标题
              type: 'map', //地图主要用于地理区域数据的可视化
              geoIndex: 0,//默认情况下，map series 会自己生成内部专用的 geo 组件。但是也可以用这个 geoIndex 指定一个 geo 组件。这样的话，map 和 其他 series（例如散点图）就可以共享一个 geo 组件了。并且，geo 组件的颜色也可以被这个 map series 控制，从而用 visualMap 来更改
              data: [{
                "name": "成华区",
                "value": 142
              },{
                "name": "武侯区",
                "value": 142
              }]
            }
          ]
        }
        //cdChart.showLoading();
        cdChart.setOption(optionMap,true);//是否不跟之前设置的 option 进行合并，默认为 false，即合并

        window.onresize=function(){
          cdChart.resize();
          //cdChart.hideLoading();
        }

      }
    }
  }
</script>

<style>

</style>
