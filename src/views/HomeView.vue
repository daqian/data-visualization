<script setup lang="ts">
import HeaderCondition from './../components/HeaderCondition.vue'
import CurveChart from './../components/CurveChart.vue'
import MultipleLineChart from './../components/MultipleLineChart.vue'
import LineChart from './../components/LineChart.vue'
import MultipleLineChartOne from './../components/MultipleLineChartOne.vue'
import MultipleLineChartTwo from './../components/MultipleLineChartTwo.vue'
import MultipleLineChartThree from './../components/MultipleLineChartThree.vue'
</script>
<template>
  <div class="wrapper">
    <HeaderCondition />
    <div class="content">
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
      <div class="right-side">
        <div class="param-config">Param Config</div>
        <div class="hole-size">Hole Size</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
}
.content {
  display: flex;
}
.chart-wrapper {
  width: 1200px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
.right-side {
  display: flex;
  flex-direction: column;
}
.param-config {
  height: 200px;
}
.hole-size {

}
.chart-box {
  margin: 20px;
}
</style>
