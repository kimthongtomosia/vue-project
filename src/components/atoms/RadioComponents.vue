<template>
  <label class="radio">
    <input
      type="radio"
      :value="value"
      :checked="modelValue === value"
      @change="$emit('update:modelValue', value)"
    />
    <span class="radio__label"><slot></slot></span>
  </label>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import type { PropType } from 'vue'
export default defineComponent({
  name: 'ARadio',
  props: {
    value: {
      type: [String, Number] as PropType<string | number>,
      required: true,
    },
    modelValue: {
      type: [String, Number] as PropType<string | number>,
      required: true,
    },
  },
  emits: ['update:modelValue'],
})
</script>
