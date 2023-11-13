<template>
  <div>
    <div ref="echarts" class="raderchart"></div>
  </div>
</template>

<script>
import * as echarts from 'echarts';

export default {

  mounted() {
    // 基于准备好的DOM，初始化ECharts实例
    const myChart = echarts.init(this.$refs.echarts, 'dark');

    const option = {
      legend: {
        data: ['test1', 'test2'],
          selectedMode:'multiple',
          top:'10%'
      },
      radar: {
        indicator: [
          { name: '1', max: 6500 },
          { name: '2', max: 16000 },
          { name: '3', max: 30000 },
          { name: '4', max: 38000 },
          { name: '5', max: 52000 },
          { name: '6', max: 25000 },
        ],
          center:['50%','50%'],
      },
        backgroundColor:'transparent',
      series: [
        {
          name: 'test1 vs test2',
          type: 'radar',
          data: [
            {
              value: [4200, 3000, 20000, 35000, 50000, 18000],
              name: 'test1',
            },
            {
              value: [5000, 14000, 28000, 26000, 42000, 21000],
              name: 'test2',
            },
          ],
        },
      ],
    };

    // 使用刚指定的配置项和数据显示图表
    myChart.setOption(option);
  },
};
</script>
<style>
    .raderchart{
        height: 500px;
        width:300px;
        position: absolute;
        top: 10px;
        left: 15px;
    }
</style>
