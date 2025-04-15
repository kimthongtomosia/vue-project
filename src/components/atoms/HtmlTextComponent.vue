<template>
  <div class="html-text">
    <section class="html-text__section">
      <h2 class="html-text__title">Sử dụng v-html</h2>
      <div v-html="htmlString" class="html-text__content html-text__content--html"></div>
    </section>

    <hr class="html-text__separator" />

    <section class="html-text__section">
      <h2 class="html-text__title">Sử dụng v-text</h2>
      <p v-text="textContent" class="html-text__content html-text__content--text"></p>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const htmlString = ref(
  '<strong>Xin chào từ v-html!</strong> <span style="color: blue;">Đây là một đoạn HTML.</span>',
)
const textContent = ref('Đây là một đoạn text được hiển thị bằng v-text.')
</script>

<style lang="scss" scoped>
@import '@/assets/sass/html-text.scss';
</style>
