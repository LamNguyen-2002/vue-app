<script setup>
// Import các thư viện cần thiết
import { ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'

// Import dữ liệu media
import video from '@/assets/video.mp4'
import thumnail from '@/assets/logo MTT.png'

// Danh sách các slide (có thể là ảnh hoặc video)
const slides = [
    { id: 1, thumb: thumnail, src: video },
    { id: 2, thumb: thumnail, src: video },
    { id: 3, thumb: thumnail, src: video },
]

// Trạng thái hiển thị modal video
const showModal = ref(false)
// Slide đang được chọn để hiển thị trong modal
const selectedSlide = ref(null)
// ID của slide đang được hover (dùng để hiển thị thông tin dưới ảnh)
const hoveredId = ref(null)

// Hàm mở modal khi click vào thumb
const openModal = (slide) => {
    selectedSlide.value = slide
    showModal.value = true
}
</script>

<template>
  <!-- Swiper hiển thị các slide, mỗi slide là một ảnh thumb -->
  <Swiper :slides-per-view="1" :centered-slides="true" space-between="16" grab-cursor="true" class="my-swiper" id="slide-swiper">
    <SwiperSlide v-for="slide in slides" :key="slide.id" class="slide-item" :id="`slide-item-${slide.id}`">
      <!-- Bọc ảnh và box info trong 1 div để căn giữa và xử lý hover -->
    <div class="slide-item">
      <div class="thumb-wrapper" @mouseenter="hoveredId = slide.id" @mouseleave="hoveredId = null">
        <img
          :src="slide.thumb"
          :alt="slide.title"
          class="thumb-img"
          :id="`thumb-img-${slide.id}`"
          @click="openModal(slide)"
        />
        <transition name="fade">
          <div v-if="hoveredId === slide.id" class="thumb-info" :id="`thumb-info-${slide.id}`">
            Mặc cảm là khi bạn luôn thấy mình thấp kém, không đủ tốt, không xứng đáng với tình yêu hay thành công. Bạn né tránh ánh nhìn của người khác, sợ bị đánh giá, và luôn thu mình trong vỏ bọc an toàn.

Hệ quả: Bạn tự giới hạn bản thân, đánh mất nhiều cơ hội và dần quên mất con người thật sự bên trong mình.

Giải pháp: Nâng Tầm giúp bạn nhìn lại gốc rễ cảm giác “không đủ tốt” và từng bước xây lại sự tự tin thật sự từ bên trong.
          </div>
        </transition>
      </div>
    </div>
    </SwiperSlide>
  </Swiper>

  <!-- Modal pop-up hiển thị video khi click vào thumb -->
  <div v-if="showModal" class="modal-overlay" id="slide-modal-overlay" @click.self="showModal = false">
    <div class="modal-box" id="slide-modal-box">
      <video v-if="selectedSlide" :src="selectedSlide.src" controls playsinline preload="metadata" class="video-player" :id="`slide-video-${selectedSlide.id}`" />
    </div>
  </div>
</template>

<style scoped>
/* Swiper căn giữa các slide */
.my-swiper {
  padding: 12px 0 24px 0;
  width: 100%;
  box-sizing: border-box;
}
.my-swiper .swiper-wrapper {
  justify-content: center;
  display: flex;
}

/* Slide item chỉ vừa đủ chứa ảnh, căn giữa */
.slide-item {
  display: flex;
  justify-content: center;
  align-items: center;
  width: auto;
  min-width: 0;
  height: auto;
  padding: 0;
  text-align: center;
}

/* Ảnh thumb lớn, bo góc, hiệu ứng hover */
.thumb-img {
  width: auto;
  max-width: 98vw;
  max-height: 320px;
  margin-left: auto;
  margin-right: auto;
  display: block;
  border-radius: 18px;
  cursor: pointer;
  transition: transform 0.3s cubic-bezier(.4,2,.6,1), box-shadow 0.2s;
  box-shadow: 0 2px 16px rgba(44,62,80,0.09);
  background: #fff;
}


/* Info hover đè lên phần dưới ảnh, không đẩy layout */
.thumb-wrapper {
  position: relative;
  display: inline-block;
}

/* Hiển thị bên dưới ảnh nhưng đè lên nội dung dưới */
.thumb-info {
  position: absolute;
  top: 100%; /* nằm ngay dưới ảnh */
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0,0,0,0.9);
  color: white;
  padding: 1em;
  border-radius: 10px;
  font-size: 0.95em;
  white-space: normal;
  word-break: break-word;
  z-index: 999;
  width: 280px;
  max-width: 90vw;
  box-shadow: 0 4px 16px rgba(0,0,0,0.3);
  pointer-events: none; /* để không làm gián đoạn hover */
  text-align: left;
}

/* Fade animation */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

/* Hiệu ứng fade in/out cho box info */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}

/* Modal hiển thị video */
.modal-overlay {
  position: fixed;
  top: 0; left: 0; width: 100vw; height: 100vh;
  background: rgba(0,0,0,0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  padding: 0 0.5em;
}
.modal-box {
  background: #fff;
  padding: 1.2em 0.7em;
  border-radius: 18px;
  width: 100%;
  max-width: 420px;
  text-align: center;
  box-shadow: 0 6px 32px rgba(44,62,80,0.13);
  display: flex;
  flex-direction: column;
  align-items: center;
}
.video-player {
  width: 100%;
  max-width: 420px;
  border-radius: 18px;
  box-shadow: 0 4px 20px rgba(44,62,80,0.13);
  background: black;
}

/* Responsive cho mobile */
@media (max-width: 700px) {
  .my-swiper {
    padding: 8px 0 16px 0;
    min-height: 180px;
  }
  .slide-item {
    height: 140px;
  }
  .thumb-img {
    max-width: 98vw;
    max-height: 220px;
    border-radius: 14px;
  }
  .modal-box {
    padding: 0.7em 0.2em;
    border-radius: 12px;
    max-width: 98vw;
  }
  .video-player {
    max-width: 98vw;
    border-radius: 12px;
  }
}
</style>
