<script setup lang="ts">
import { ref } from 'vue'
import type { Ref } from 'vue'
import { ElSelectV2, ElButton, ElDropdown, ElDropdownMenu, ElDropdownItem, ElIcon, ElButtonGroup } from 'element-plus'
import type {SelectOption} from "@/lib/interfaces";

const value: Ref<number> = ref<number>(0)
const options: SelectOption[] = [
  {
    value: 0,
    label: '主井筒'
  },
  {
    value: 1,
    label: "井筒2"
  }
]


</script>

<template>
  <div class="header-condition">
    <div class="condition-element">
      <el-button-group>
        <el-button type="primary" class="toggle-button active">历史</el-button>
        <el-button type="primary" class="toggle-button">
          实时
        </el-button>
      </el-button-group>
    </div>
    <div class="condition-element">
      <el-select-v2
          v-model="value"
          :options="options"
          placeholder="Please select"
          size="large"
      />
    </div>
    <div>

      <el-dropdown>
    <span class="el-dropdown-link">
      图像选择
      <el-icon class="el-icon--right">
        <arrow-down />
      </el-icon>
    </span>
        <template #dropdown>
          <el-dropdown-menu>
            <el-dropdown-item>Action 1</el-dropdown-item>
            <el-dropdown-item>Action 2</el-dropdown-item>
            <el-dropdown-item>Action 3</el-dropdown-item>
            <el-dropdown-item disabled>Action 4</el-dropdown-item>
            <el-dropdown-item divided>Action 5</el-dropdown-item>
          </el-dropdown-menu>
        </template>
      </el-dropdown>
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
