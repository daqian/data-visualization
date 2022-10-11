<script setup lang="ts">
import HeaderCondition from './../components/HeaderCondition.vue'
import CurveChart from './../components/CurveChart.vue'
import MultipleLineChart from './../components/MultipleLineChart.vue'
import LineChart from './../components/LineChart.vue'
import MultipleLineChartOne from './../components/MultipleLineChartOne.vue'
import MultipleLineChartTwo from './../components/MultipleLineChartTwo.vue'
import MultipleLineChartThree from './../components/MultipleLineChartThree.vue'

const onConditionChange = function (condition: any) {
  console.log(condition);
}
</script>
<template>
  <div class="wrapper">
    <HeaderCondition @onConditionChange="onConditionChange" />
    <div class="content">
      <div class="chart-wrapper">
        <div class="chart-box">
          <CurveChart />
          <div>最小循环周</div>
        </div>
        <div class="chart-box">
          <MultipleLineChart />
          <div>最小循环时间</div>
        </div>
        <div class="chart-box">
          <LineChart />
          <div>岩屑床高度</div>
        </div>
        <div class="chart-box">
          <MultipleLineChartOne />
          <div>环空流速</div>
        </div>
        <div class="chart-box">
          <MultipleLineChartTwo />
          <div>携岩指数（CCI）</div>
        </div>
        <div class="chart-box">
          <MultipleLineChartThree />
          <div>岩屑浓度百分比</div>
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
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
