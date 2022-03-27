<script setup>
import { mixColor } from '@/utils';
import { useCssVar } from '@vueuse/core'

const themeColor = useCssVar('--color-primary')
const handleChangeTheme = (color) => {
  useCssVar('--color-primary').value = color
  useCssVar('--el-color-primary').value = color
  for (let i = 1; i <= 9; i++) {
    useCssVar(`--el-color-primary-light-${i}`).value = mixColor(color, '#ffffff', i / 10)
    useCssVar(`--el-color-primary-dark-${i}`).value = mixColor(color, '#000000', 2 / 10)
  }
}
</script>

<template>
  <div class="page">
    <div class="text">主题色文字</div>
    <el-button type="primary">主题色按钮</el-button>
    <div>
      <span>修改主题色：</span>
      <el-color-picker v-model="themeColor" @change="handleChangeTheme" />
    </div>
  </div>
</template>

<style lang="scss">
  .page {
    .text {
      color: var(--color-primary);
    }
  }
</style>
