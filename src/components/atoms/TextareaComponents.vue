<template>
  <textarea
    class="textarea"
    :value="modelValue"
    @input="$emit('update:modelValue', ($event.target as HTMLTextAreaElement).value)"
    :rows="rows"
  ></textarea>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import type { PropType } from 'vue'

export default defineComponent({
  name: 'ATextarea',
  props: {
    modelValue: {
      type: String as PropType<string>,
      default: '',
    },
    rows: {
      type: Number as PropType<number>,
      default: 3,
    },
  },
  emits: ['update:modelValue'],
})
</script>
