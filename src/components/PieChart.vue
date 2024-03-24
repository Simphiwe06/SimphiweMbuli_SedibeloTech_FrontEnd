<template>
  <div class="pie-chart-container">
    <div class="chart-header">
      <h2 class="chart-title">Installation Trends Over Years</h2>
      <p class="chart-description"><strong>This pie chart illustrates the trend of software installations over the past few years.</strong></p>
    </div>
    <div class="chart">
      <canvas ref="chartCanvas"></canvas>
    </div>
    <div class="legend">
      <div v-for="(item, index) in data" :key="index" class="legend-item">
        <span class="legend-circle" :style="{ backgroundColor: colors[index] }"></span>
        <span class="legend-label"><strong>{{ item.year }}</strong></span>
      </div>
    </div>
  </div>
</template>

<script>
import Chart from 'chart.js';

export default {
  name: 'PieChart',
  props: ['data'],
  data() {
    return {
      colors: ['#FF6384', '#36A2EB', '#FFCE56', '#4BC0C0', '#9966FF'] // Update colors as needed
    };
  },
  mounted() {
    this.renderChart();
  },
  methods: {
    renderChart() {
      const ctx = this.$refs.chartCanvas.getContext('2d');
      new Chart(ctx, {
        type: 'pie',
        data: {
          labels: this.data.map(item => item.year),
          datasets: [{
            data: this.data.map(item => item.numInstalls),
            backgroundColor: this.colors
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          legend: {
            display: false 
          }
        }
      });
    }
  }
};
</script>

<style scoped src="./PieChart.css"></style>
