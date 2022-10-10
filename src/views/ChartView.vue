<script setup lang="ts">
import CurveChart from './../components/CurveChart.vue'
import MultipleLineChart from './../components/MultipleLineChart.vue'
import LineChart from './../components/LineChart.vue'
import MultipleLineChartOne from './../components/MultipleLineChartOne.vue'
import MultipleLineChartTwo from './../components/MultipleLineChartTwo.vue'
import MultipleLineChartThree from './../components/MultipleLineChartThree.vue'
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
    <div class="chart-box">
      <MultipleLineChartOne />
    </div>
    <div class="chart-box">
      <MultipleLineChartTwo />
    </div>
    <div class="chart-box">
      <MultipleLineChartThree />
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .chart-wrapper {
    width: 1200px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }
  .chart-box {
    margin: 20px;
  }
}
</style>
