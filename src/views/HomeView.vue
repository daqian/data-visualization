<script setup lang="ts">
import HeaderCondition from "./../components/HeaderCondition.vue";
import CurveChart from "./../components/CurveChart.vue";
import MultipleLineChart from "./../components/MultipleLineChart.vue";
import LineChart from "./../components/LineChart.vue";
import MultipleLineChartOne from "./../components/MultipleLineChartOne.vue";
import MultipleLineChartTwo from "./../components/MultipleLineChartTwo.vue";
import MultipleLineChartThree from "./../components/MultipleLineChartThree.vue";
import { ref, Ref } from "vue";
import { DataTypeValue } from "@/lib/enums";

let selectImageValues: Ref<number[]> = ref<number[]>([0, 1, 2, 3, 4, 5, 6]);
const onConditionChange = function (condition: any) {
  console.log(condition);
  if (condition.selectImageValues) {
    selectImageValues.value = condition.selectImageValues;
  }
};
</script>
<template>
  <div class="wrapper">
    <HeaderCondition @onConditionChange="onConditionChange" />
    <div class="content">
      <div class="chart-wrapper">
        <div class="chart-box" v-if="selectImageValues.includes(0)">
          <CurveChart />
          <div>最小循环周</div>
        </div>
        <div class="chart-box" v-if="selectImageValues.includes(1)">
          <MultipleLineChart />
          <div>最小循环时间</div>
        </div>
        <div class="chart-box" v-if="selectImageValues.includes(2)">
          <LineChart />
          <div>岩屑床高度</div>
        </div>
        <div class="chart-box" v-if="selectImageValues.includes(3)">
          <MultipleLineChartOne />
          <div>环空流速</div>
        </div>
        <div class="chart-box" v-if="selectImageValues.includes(4)">
          <MultipleLineChartTwo />
          <div>携岩指数（CCI）</div>
        </div>
        <div class="chart-box" v-if="selectImageValues.includes(5)">
          <MultipleLineChartThree />
          <div>岩屑浓度百分比</div>
        </div>
      </div>
      <div class="right-side">
        <div class="param-config">计算参数配置</div>
        <div class="hole-size">井眼尺寸</div>
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
  height: 400px;
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
