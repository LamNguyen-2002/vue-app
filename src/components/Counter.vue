<template>
  <div class="counter-box" id="counter">
    <p class="counter-value" id="counter-value">Giá trị: <span>{{ count }}</span></p>
    <div class="counter-controls">
      <button @click="increment" id="counter-increment">Tăng</button>
      <button @click="decrement" id="counter-decrement">Giảm</button>
      <button @click="resetCount" class="reset-btn" id="counter-reset">Đặt lại</button>
    </div>
    <div class="counter-info">
      <p class="counter-info-title">Thông tin:</p>
      <div class="counter-details">
        <p class="counter-double" id="counter-double">Gấp đôi: <span>{{ doubled }}</span></p>
        <p class="counter-half" id="counter-half">Một nửa: <span>{{ half }}</span></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0 // Biến lưu giá trị đếm
    }
  },
  methods: {
    increment() { // Hàm tăng giá trị count lên 1
      this.count++
    },
    // Hàm giảm giá trị count xuống 1
    decrement() {
      this.count--
    },
    resetCount() { // Hàm đặt lại giá trị count về 0
      this.count = 0
    }
  },
  computed: {
    // Tự động tính toán lại khi count thay đổi
    doubled() {
      return this.count * 2 // Trả về giá trị gấp đôi của count
    },
    half() {
      return this.count / 2 // Trả về giá trị một nửa của count
    }
  }
}
</script>

<style scoped>
.counter-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.2em;
  width: 100%;
}
.counter-value {
  font-size: 1.25em;
  font-weight: 700;
  margin-bottom: 0.5em;
}
.counter-value span, .counter-double span, .counter-half span {
  color: #4f8cff;
  font-weight: 800;
  font-size: 1.3em;
}
.counter-controls {
  display: flex;
  flex-direction: column;
  gap: 0.7em;
  width: 100%;
}
.counter-controls button {
  width: 100%;
  font-size: 1.1em;
  padding: 1em 0;
  border-radius: 14px;
  font-weight: 700;
}
.reset-btn {
  background: linear-gradient(90deg, #ff7875 0%, #ffb86c 100%);
  color: #fff;
}
.counter-info {
  width: 100%;
  margin-top: 1.2em;
}
.counter-info-title {
  font-size: 1.05em;
  font-weight: 600;
  color: #38c6ff;
  margin-bottom: 0.5em;
  text-align: left;
}
.counter-details {
  display: flex;
  flex-direction: row;
  /* justify-content: space-between; */
  justify-content: center;
  gap: 1.2em;
  width: 100%;
}
.counter-double, .counter-half {
  font-size: 1.1em;
  font-weight: 600;
  text-align: center;
}
.my-swiper .swiper-wrapper {
  justify-content: center;
  display: flex;
}
@media (max-width: 700px) {
  .counter-box {
    gap: 0.7em;
  }
  .counter-controls button {
    font-size: 1em;
    padding: 0.9em 0;
  }
  .counter-details {
    flex-direction: column;
    gap: 0.5em;
    align-items: center;
  }
}
</style>
