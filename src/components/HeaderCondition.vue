<script setup lang="ts">
import type {Ref} from 'vue'
import {ref} from 'vue'
import type {SelectOption} from "@/lib/interfaces";
import {DataTypeLabel, DataTypeValue} from "@/lib/enums";
import { ElSelectV2, ElButton, ElButtonGroup } from 'element-plus'

let dataTypeValue: Ref<DataTypeValue> = ref<DataTypeValue>(DataTypeValue.History);
const dataTypeOptions: SelectOption[] = [
  {
    value: DataTypeValue.History,
    label: DataTypeLabel.History
  },
  {
    value: DataTypeValue.RealTime,
    label: DataTypeLabel.RealTime
  }
]

const selectHoleValue: number = 0
const selectHoleOptions: SelectOption[] = [
  {
    value: 0,
    label: '主井筒'
  },
  {
    value: 1,
    label: "井筒2"
  }
]

const selectImageValues: SelectOption[] = [];
const selectImageOptions: SelectOption[] = [
  {
    value: 0,
    label: '最小循环周'
  },
  {
    value: 1,
    label: "最小循环时间"
  },
  {
    value: 2,
    label: "岩屑床高度"
  },
  {
    value: 3,
    label: "环空流速"
  },
  {
    value: 4,
    label: "携岩指数（CCI）"
  },
  {
    value: 5,
    label: "岩屑浓度百分比"
  }
]

const toggleDataType = (value: DataTypeValue) => {
  dataTypeValue.value = value;

}
</script>

<template>
  <div class="header-condition">
    <div class="condition-element">
      <el-button-group>
        <el-button type="primary"
                   class="toggle-button"
                   :class="{ active: dataTypeValue === option.value }" @click="toggleDataType(option.value)" v-for="option in dataTypeOptions">
          {{ option.label }}
        </el-button>
      </el-button-group>
    </div>
    <div class="condition-element">
      <el-select-v2
          v-model="selectHoleValue"
          :options="selectHoleOptions"
          placeholder="Please select"
          style="width: 120px"
      />
    </div>
    <div class="condition-element">
      <el-select-v2
          v-model="selectImageValues"
          :options="selectImageOptions"
          placeholder="图像选择"
          style="width: 240px"
          multiple
      />
    </div>
  </div>
</template>

<style scoped>
.header-condition {
  display: flex;
  margin-top: 10px;
  margin-bottom: 10px;
}
.condition-element {
  margin-left: 10px;

}
  .toggle-button {
    margin: 0;
    border-radius: 0;
    border: solid 1px #444;
    background-color: #ffffff;
    color: #444;
  }
  .toggle-button.active {
    background-color: #444;
    color: #ffffff;
  }
</style>
