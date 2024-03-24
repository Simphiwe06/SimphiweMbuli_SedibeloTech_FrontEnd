<template>
  <div id="app">
    <PieChart :data="chartData" />
  </div>
</template>

<script>
import PieChart from './components/PieChart.vue';
import pieChartData from '../public/pieChart.json';

export default {
  name: 'App',
  components: {
    PieChart
  },
  data() {
    return {
      chartData: pieChartData
    };
  }
};
</script>

<style>
/* Add global styles here if needed */
</style>