<script setup lang="ts">
import Chart from './../components/Chart.vue'
import LineChart from './../components/LineChart.vue'
import CurveChart from './../components/CurveChart.vue'
</script>
<template>
  <div class="chart-wrapper">
    <div class="chart-box">
      <Chart />
    </div>
    <div class="chart-box">
      <LineChart />
    </div>
    <div class="chart-box">
      <CurveChart />
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .chart-wrapper {
    display: flex;
  }
  .chart-box {
    margin: 20px;
  }
}
</style>
