<template>
  <div>
    <v-select v-model="selectedDate" @input="updateChart">
      <v-list-item v-for="date in dates" :key="date" :value="date">{{ date }}</v-list-item>
    </v-select>
    <line-chart :data="chartData" :options="chartOptions"></line-chart>
  </div>
</template>

<script>
import { Line } from 'vue-chartjs'
import axios from 'axios'

export default {
  components: {
    'line-chart': Line
  },
  data() {
    return {
      selectedDate: '',
      chartData: {},
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          title: {
            display: true,
            text: '折线图'
          },
          legend: {
            display: true,
            position: 'top'
          }
        },
        scales: {
          xAxes: [{
            type: 'time',
            distribution: 'series',
            time: {
              unit: 'hour'
            }
          }],
          yAxes: [{
            ticks: {
              beginAtZero: true
            }
          }]
        }
      }
    }
  },
  methods: {
    async fetchData(date) {
      const response = await axios.get(`/api/data?date=${date}`)
      return response.data
    },
    updateChart() {
      this.fetchData(this.selectedDate).then(data => {
        this.chartData = {
          labels: ['00:00', '01:00', '02:00', '03:00', '04:00', '05:00', '06:00', '07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00', '14:00', '15:00', '16:00', '17:00', '18:00', '19:00', '20:00', '21:00', '22:00', '23:00'],
          datasets: [{
            label: '数据',
            data: data.slice(2, 15),
            fill: false,
            borderColor: 'rgb(75, 192, 192)',
            tension: 0.1
          }]
        }
      })
    }
  },
  mounted() {
    this.dates = ['2022-01-01', '2022-01-02', '2022-01-03'] // 这里替换为你的日期列表
    this.updateChart()
  }
}
</script>
