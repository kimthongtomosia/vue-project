<template>
  <input
    class="input"
    :type="type"
    :value="modelValue"
    @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)"
    v-bind="$attrs"
  />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import type { PropType } from 'vue'
export default defineComponent({
  name: 'AInput',
  props: {
    type: {
      type: String as PropType<string>,
      default: 'text',
    },
    modelValue: {
      type: [String, Number] as PropType<string | number>,
      default: '',
    },
  },
  emits: ['update:modelValue'],
})
</script>
