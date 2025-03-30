<template>
  <button
    ref="_ref"
    class="cr-button"
    :class="{
      [`cr-button--${type}`]: type,
      [`cr-button--${size}`]: size,
      'is-round': round,
      'is-circle': circle,
      'is-plain': plain,
      'is-disabled': disabled,
    }"
    :disabled="disabled"
    :autofocus="autofocus"
    :type="nativeType"
  >
    <span><slot></slot></span>
  </button>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import type { ButtonProps } from './types'
// defineProps<ButtonProps>()

// defineOptions 定义组件属性
defineOptions({
  name: 'CRButton',
})

// 设置默认值
withDefaults(defineProps<ButtonProps>(), {
  nativeType: 'button',
})

// <button ref="_ref"></button>  用于获取该dom节点
// defineExpose暴露组件的属性，这里把该组件暴露出去
const _ref = ref<HTMLButtonElement>()
defineExpose({
  ref: _ref,
})
</script>

<style>
.cr-button {
  /* --main-bg-color: yellow;覆盖颜色 */
  background-color: var(--main-bg-color);
}
</style>
