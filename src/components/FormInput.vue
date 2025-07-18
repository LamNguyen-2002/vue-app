<template>
  <div class="form-input-box">
    <label for="user-input" class="form-label">Nhập tên của bạn</label>
    <input id="user-input" v-model="inputValue" placeholder="Nhập tên của bạn" class="form-input" type="text" autocomplete="off">
  </div>
</template>

<script>
export default {
  props: ['modelValue'], // Nhận giá trị v-model từ component cha
  emits: ['update:modelValue'], // Khai báo sự kiện để cập nhật giá trị lên cha
  computed: {
    inputValue: {
      // Getter: trả về giá trị modelValue từ cha
      get() {
        return this.modelValue
      },
      // Setter: phát sự kiện update:modelValue khi giá trị thay đổi
      set(val) {
        this.$emit('update:modelValue', val)
      }
    }
  }
}
</script>

<style scoped>
.form-input-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1em;
  width: 100%;
}
.form-label {
  font-size: 1.15em;
  color: #4f8cff;
  font-weight: 700;
  margin-bottom: 0.3em;
  letter-spacing: 0.5px;
}
.form-input {
  width: 100%;
  max-width: 350px;
  font-size: 1.1em;
  border-radius: 12px;
  padding: 1em 1.2em;
  border: 2px solid var(--color-border);
  background: var(--color-background-mute);
  transition: border 0.2s, box-shadow 0.2s;
}
.form-input:focus {
  border: 2px solid #4f8cff;
  box-shadow: 0 2px 12px rgba(44, 62, 80, 0.13);
}
@media (max-width: 700px) {
  .form-label {
    font-size: 1em;
  }
  .form-input {
    font-size: 1em;
    padding: 0.9em 1em;
  }
}
</style>
