<template>
  <select
    class="select"
    :value="modelValue"
    @change="$emit('update:modelValue', ($event.target as HTMLSelectElement).value)"
  >
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.label }}
    </option>
  </select>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import type { PropType } from 'vue'
interface SelectOption {
  value: string | number
  label: string
}

export default defineComponent({
  name: 'ASelect',
  props: {
    modelValue: {
      type: [String, Number] as PropType<string | number>,
    },
    options: {
      type: Array as PropType<SelectOption[]>,
      required: true,
      validator: (options: SelectOption[]) =>
        options.every((option) => 'value' in option && 'label' in option),
    },
  },
  emits: ['update:modelValue'],
})
</script>
