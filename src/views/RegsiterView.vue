<template>
  <div class="register-view">
    <h1 class="register-view__title">Đăng ký tài khoản</h1>

    <form class="register-view__form" @submit.prevent="handleSubmit">
      <div class="form-group">
        <label>Họ và tên</label>
        <a-input v-model="formData.fullName" placeholder="Nhập họ tên" class="custom-input" />
      </div>

      <div class="form-group">
        <label>Giới tính</label>
        <div class="radio-group">
          <a-radio v-model="formData.gender" value="male">Nam</a-radio>
          <a-radio v-model="formData.gender" value="female">Nữ</a-radio>
        </div>
      </div>

      <div class="form-group">
        <a-checkbox v-model="formData.agreeTerms"> Tôi đồng ý với điều khoản </a-checkbox>
      </div>
      <div class="form-group">
        <label>Quốc gia</label>
        <a-select
          v-model="formData.country"
          :options="countryOptions"
          placeholder="Chọn quốc gia"
          class="custom-select"
        />
      </div>

      <div class="form-group">
        <label>Giới thiệu bản thân</label>
        <a-textarea
          v-model="formData.bio"
          placeholder="Mô tả về bạn..."
          :rows="4"
          class="custom-textarea"
        />
      </div>

      <button type="submit" class="register-view__submit">Đăng ký</button>
    </form>

    <div v-if="showData" class="register-view__data">
      <h3>Dữ liệu đã nhập:</h3>
      <pre>{{ formData }}</pre>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue'
import AInput from '@/components/atoms/InputComponents.vue'
import ARadio from '@/components/atoms/RadioComponents.vue'
import ACheckbox from '@/components/atoms/CheckboxesComponents.vue'
import ASelect from '@/components/atoms/SelectComponents.vue'
import ATextarea from '@/components/atoms/TextareaComponents.vue'

export default {
  name: 'RegisterView',
  components: {
    AInput,
    ARadio,
    ACheckbox,
    ASelect,
    ATextarea,
  },
  setup() {
    const formData = ref({
      fullName: '',
      gender: 'male',
      agreeTerms: false,
      country: '',
      bio: '',
    })

    const showData = ref(false)

    const countryOptions = [
      { value: 'vn', label: 'Việt Nam' },
      { value: 'us', label: 'United States' },
      { value: 'jp', label: 'Japan' },
      { value: 'kr', label: 'South Korea' },
    ]

    const handleSubmit = () => {
      if (formData.value.fullName && formData.value.country && formData.value.agreeTerms) {
        showData.value = true
      } else {
        alert('Vui lòng điền đầy đủ thông tin và đồng ý với điều khoản')
      }
    }

    return {
      formData,
      countryOptions,
      showData,
      handleSubmit,
    }
  },
}
</script>

<style lang="scss" scoped>
@import '../assets/sass/regsiter.scss';
</style>
