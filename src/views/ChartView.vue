<script setup lang="ts">
import CurveChart from './../components/CurveChart.vue'
import MultipleLineChart from './../components/MultipleLineChart.vue'
import LineChart from './../components/LineChart.vue'
</script>
<template>
  <div class="chart-wrapper">
    <div class="chart-box">
      <CurveChart />
    </div>
    <div class="chart-box">
      <MultipleLineChart />
    </div>
    <div class="chart-box">
      <LineChart />
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
