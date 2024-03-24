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
  
  <style scoped>
  /* Component container */
  .pie-chart-container {
    text-align: center;
    padding: 20px; /* Add padding for better spacing */
  }
  
  /* Chart header */
  .chart-header {
    margin-bottom: 30px; 
  }
  
  .chart-title {
    font-size: 32px; 
    font-weight: bold;
  }
  
  .chart-description {
    font-size: 18px; 
    color: #666;
  }
  
  /* Chart canvas */
  .chart canvas {
    width: 90%; 
    max-width: 600px; 
    height: auto;
    margin: auto;
    display: block;
  }
  
  /* Legend */
  .legend {
    display: flex;
    justify-content: center;
    margin-top: 30px; 
  }
  
  .legend-item {
    display: flex;
    align-items: center;
    margin-right: 30px; 
  }
  
  .legend-circle {
    width: 12px; 
    height: 12px; 
    border-radius: 50%;
    display: inline-block;
    margin-right: 8px; 
  }
  
  .legend-label {
    font-size: 18px; 
    font-weight: bold; 
  }
  
  
  body {
    background-color: #f0f0f0; 
  }
  </style>