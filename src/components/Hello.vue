<template>
<div>
   <div id="main" @click="change()"> </div>
   <div id="echarts2"></div>
   <div id="echarts3"></div>
</div>
</template>

<script>
import echarts from 'echarts'
export default {
  name: 'hello',
  data () {
    return {
      data: [],
      changeData: [15, 25, 16, 30, 20, 10],
      xAxisData: [],
      myChart: ``
    }
  },
  mounted () {
    this.echartInit1()
    this.myChart.showLoading()
    setTimeout(()=>{
      this.data = [5, 20, 36, 10, 10, 20]
      this.xAxisData = ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
      this.echartInit1()
      this.myChart.hideLoading();
    },5000)
    this.echartsInit2()
    this.echartsInit3()
  },
  methods: {
    change () {
     this.data = [15, 25, 16, 30, 20, 10]
     this.echartInit1()
    },
    echartInit1 () {
      this.myChart = echarts.init(document.getElementById('main'));
    this.myChart.setOption({
      title: { text: 'echarts入门实例'},
      toolTip: {},
      xAxis: {
        data: this.xAxisData,
      },
      yAxis: {},
      series: [
      {
        name: '销量',
        type: 'bar',
        data: this.data
      }]
     })
    },
    echartsInit2 () {
      let myCharts2 = echarts.init(document.getElementById('echarts2'));
      myCharts2.setOption({
         backgroundColor: 'rgba(0,0,0,.5)',
         textStyle: {
            color: 'rgba(255, 255, 255,1)'
        },
        visualMap: {
              // 不显示 visualMap 组件，只用于明暗度的映射
              show: false,
              // 映射的最小值为 80
              min: 80,
              // 映射的最大值为 600
              max: 600,
              inRange: {
                  // 明暗度的范围是 0 到 1
                  colorLightness: [0, 1]
              }
          },
         series : [
            {
                label: {
                    normal: {
                        textStyle: {
                            color: 'rgba(255, 255, 255, 0.3)'
                        }
                    }
                },
                labelLine: {
                    normal: {
                        lineStyle: {
                            color: 'rgba(255, 255, 255, 0.3)'
                        }
                    }
                },
                name: '访问来源',
                type: 'pie',
                radius: '55%',
                roseType: 'angle',
                itemStyle: {
                    normal: {
                        // 阴影的大小
                        shadowBlur: 200,
                        // 阴影水平方向上的偏移
                        shadowOffsetX: 0,
                        // 阴影垂直方向上的偏移
                        shadowOffsetY: 0,
                        // 阴影颜色
                        shadowColor: 'rgba(0, 0, 0, 0.5)',
                         // 设置扇形的颜色
                        color: '#c23531'
                    }
                },

                data:[
                    {
                      value:235, 
                      name:'视频广告',
                      itemStyle: {
                        normal: {
                            color: '#ccc'
                        }
                      }
                    },
                    {value:274, name:'联盟广告'},
                    {value:310, name:'邮件营销'},
                    {value:335, name:'直接访问'},
                    {value:400, name:'搜索引擎'}
                ]
            },

        ]
      })
    },
    echartsInit3 () {
      let myCharts3 = echarts.init(document.getElementById('echarts3'));
      myCharts3.option = {
        xAxis: {
               type: 'value'
         },
         yAxis: {
             type: 'value'
         },
         dataZoom: [
             {   // 这个dataZoom组件，默认控制x轴。
                 type: 'slider', // 这个 dataZoom 组件是 slider 型 dataZoom 组件
                 start: 10,      // 左边在 10% 的位置。
                 end: 60         // 右边在 60% 的位置。
             }
         ],
         series: [
             {
                 type: 'scatter', // 这是个『散点图』
                 itemStyle: {
                     normal: {
                         opacity: 0.8
                     }
                 },
                 symbolSize: function (val) {
                     return val[2] * 40;
                 },
                 data: [["14.616","7.241","0.896"],["3.958","5.701","0.955"],["2.768","8.971","0.669"],["9.051","9.710","0.171"],["14.046","4.182","0.536"],["12.295","1.429","0.962"],["4.417","8.167","0.113"],["0.492","4.771","0.785"],["7.632","2.605","0.645"],["14.242","5.042","0.368"]]
             }
         ]
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#main{
  width: 800px;
  height: 600px;
  margin: 0 auto;
  border: 1px solid #000;
}
#echarts2{
  width: 800px;
  height: 600px;
  margin: 0 auto;
  border: 1px solid #000;
}
</style>
