<template>
  <!--中国地图-->
  <div id="myChart" class="maps"></div>
</template>

<script>
  import china from 'echarts/map/json/china.json'
  export default {
    name: "chinaMap",
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
        const myChartContainer = document.getElementById('myChart');
        const myChart = this.$echarts.init(myChartContainer);
        this.$echarts.registerMap('china', china);
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
              symbol: 'image://data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADcAAAA1CAMAAADSzYN/AAAABGdBTUEAALGPC/xhBQAAACBjSFJN\n' +
              'AAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAACBFBMVEX///8UMVgUMVgUMVgU\n' +
              'MVgUMVgUMVgUMVgUMVgUMVgUMVgUMVgUMVg/jaJw9vZv9fYuaYUUMVgUMVgxbohz+PVy9/QUMVgU\n' +
              'MVh08+508u4UMVhs3txm09M1cId89ep79OoUMVgUMVh25dxv2NMUMVhAfo+B8eGA8OEUMVh64NJy\n' +
              '0ccUMViG7daF69V50sFfqKaK5cqJ48lprqVJf4h/z7mD1LwUMViL2buDzrQUMViG0raK17qW4rwU\n' +
              'MVhwrp99v6iDwqdonpMUMViZ3raa37aa2q+S0KqEvqCOyqei3ayi3aug2qqh3KuPv5lzn4qIuJaS\n' +
              'w5um052cyJmm1J6p15+t1pms1Zlni3yFq4iOroSmx42szY+uyIihuoSzzIm30Iu5zIO7zoS7zoSj\n' +
              't31dcmjBzH28x3yrsnLEyHYoQlvBwW6tsGvKwWjGvmdCVFrRwWLQwGKmnFqLiFrFr1bCrVbUtVDU\n' +
              'tVDbtkvctkvhtkbhtUbktEHnsz3osz3qsTnqsTnssDbXpDnqrzfqrzbqrzbrsDbiqjh0+vZ3+fN5\n' +
              '9+989ut+9OeB8uKE8d2H79iK7dOO686R6cmV58OY5L2c4rif4LKj3qyn26ar2aCu15qz1JK40Yu8\n' +
              'z4TBzH3FyXbJx2/OxGjSwmLWv1vZvVbdu1DguUvjt0bmtUHptD3rsjntsTb///9qC2N4AAAAh3RS\n' +
              'TlMAAQIDBAUGBwgJCgsNFrStEgwOF9/WDxG7rhJpURz06RQQjWsTI/PuFoxiF+bcbjnGuz4oQE8V\n' +
              'mnQYXWrlGjU/XjkZydbEi1xm9evV3GY+W2rDiMfj8eMyR02Sualxyfnd+PlqJvvLa/gatGjbvR30\n' +
              '6E00gXeuttHU6+Hs5PDs8/Zj2uLh3o2QFe1rAAAAAWJLR0QAiAUdSAAAAAd0SU1FB+MFCgcdL6qr\n' +
              '61gAAAMoSURBVEjHlZZVe9RAFIa728hGkATIQLAMBAgEl4VCg7u7u7u7Q4HiUtxdfyVnZiKb7G4z\n' +
              'fa8mF9/zHZvMaWjIUIhp6ABMUSx2TMk0xUagyLS8MiISKETKKQQZqERRAkRRoEJOmSBIklwCZEkk\n' +
              'lhxCKhMlWVE1TVNVoiSOXDpRKqma3qlzl66GppSIMNeQ2oHMMLt1b23tYZmGWpIgRw4dlVmo512g\n' +
              'F7IMVRaFPEMapawYlt37HqUPMg1Fzo2U2Wkm6tvvPqW/g0yNRdre7FA7VcfOgAchA13MDIvtTGxo\n' +
              'Z9mDBj8MGeLZxFCkM1esM3ex3dBHMcMcrENNSf+Tia2dne0PfxwzwrMt0gyYOUBg41PI6BoFKCZ2\n' +
              'Rj6pYBSUBoQlGQC1IFQVl4RJ7LzRTysY47vYNGDmFIBNbFpIw4TeOWOfpRjnudgydd0YP0FTQSlm\n' +
              '5iesCipPbEsxqans2gjjyW1tU3SIODsGoCNNcP3m5ymagyav7DhTyXmapWcHNgwTO9NfZJgRzGzy\n' +
              '/VnkOBsRYWpgozC9OS8zzA2Aeew8H7qiyJWGcZgLXmVYSHSL2HlxOLCxYRzmktdVLA2CZdF5uZs2\n' +
              'jMNc8aaKlUGwKjqvLiMTMkzpoOmuv+ZtFWuDdcnHemKYBBqFueFdDYKNyXlTGemqHBnS2SRN3/y+\n' +
              'Blu2JudtvmtBZSIdTQ9mc/uHGuzYWfGxy8FJoFEXdu/5mMderyLQKL19n3LZf4AEGunI1YP0Dn7O\n' +
              '51AUKC0LS+/wl3yO0IoKjZBgdGWPHvuaz3H4V4UJRmU58Y2Hk3GC0VU/9Z2H07SDQqzDzpkfPJyN\n' +
              'Ri32O/eTh/NZnXvhFw8XQZfESep56TcPl2xTS+nQ5T88XEGJjvTdwFf/8nAN60n/IEHNvP6PC1NT\n' +
              'pEQHb8ONmy238mi5fQceb/YTTfYBbLtO2fP8Wnjw/3VtTJcF9tMO1xayf5gWRsiuAyIvhcbeQ3px\n' +
              'K/Ydw9DNesDrQt6W5FEqhPuVLJcURVXJtlSNSh4zeAilirWtkOxzcnuwZa9i2wv3R7JAivWhu2V6\n' +
              'uQz3Vbax1qXWUlHghwn+A9llf2IKlRvMAAAAJXRFWHRkYXRlOmNyZWF0ZQAyMDE5LTA1LTA5VDIz\n' +
              'OjI5OjQ3KzA4OjAwS2e8mAAAACV0RVh0ZGF0ZTptb2RpZnkAMjAxOS0wNS0wOVQyMzoyOTo0Nysw\n' +
              'ODowMDo6BCQAAAAZdEVYdFNvZnR3YXJlAEFkb2JlIEltYWdlUmVhZHlxyWU8AAAAAElFTkSuQmCC',
              symbolSize: 30,//标记点大小
              symbolOffset: ['0', '-80%'],//标记点位置
              data: [{//标记点数据
                name: '我是成都的经纬度',
                value: [104.06, 30.67]
              }
              ],
            },{
              name: '启动次数', //浮动框的标题
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
        //myChart.showLoading();
        myChart.setOption(optionMap,true);//是否不跟之前设置的 option 进行合并，默认为 false，即合并

        window.onresize=function(){
          myChart.resize();
          //myChart.hideLoading();
        }

      }
    }
  }
</script>

<style>

</style>
