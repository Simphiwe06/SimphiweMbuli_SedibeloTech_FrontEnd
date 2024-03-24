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
/* Global styles */
body {
  font-family: Arial, sans-serif; /* Use a commonly available font */
}
</style>