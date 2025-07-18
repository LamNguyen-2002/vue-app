<template>
  <div>
    <!-- Nút mở modal -->
    <button @click="showModal = true" class="open-btn" id="popup-open">Mở Pop-up</button>

    <!-- Modal -->
    <div v-if="showModal" class="modal-overlay" id="popup-overlay" @click.self="showModal = false">
      <div class="modal-box" id="popup-box">
        <h2>Đây là pop-up</h2>
        <video controls>
          <source src="@/assets/video.mp4" type="video/mp4">
        </video>
        <button @click="showModal = false" class="close-btn" id="popup-close">Đóng</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const showModal = ref(false)
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0; left: 0; width: 100vw; height: 100vh;
  background: rgba(0,0,0,0.5);
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
  max-width: 400px;
  text-align: center;
  box-shadow: 0 6px 32px rgba(44,62,80,0.13);
  display: flex;
  flex-direction: column;
  align-items: center;
}
.open-btn,
.close-btn {
  padding: 1em 0;
  margin-top: 1em;
  border: none;
  border-radius: 14px;
  background: linear-gradient(90deg, #4f8cff 0%, #38c6ff 100%);
  color: #fff;
  font-size: 1.1em;
  font-weight: 700;
  width: 100%;
  box-shadow: 0 2px 12px rgba(44,62,80,0.10);
  transition: background 0.2s, box-shadow 0.2s, transform 0.1s;
  cursor: pointer;
}
.open-btn:hover, .close-btn:hover {
  background: linear-gradient(90deg, #38c6ff 0%, #4f8cff 100%);
  box-shadow: 0 4px 20px rgba(44,62,80,0.15);
  transform: translateY(-2px) scale(1.03);
}
.close-btn {
  background: linear-gradient(90deg, #ff7875 0%, #ffb86c 100%);
  color: #fff;
}
@media (max-width: 700px) {
  .modal-box {
    padding: 0.7em 0.2em;
    border-radius: 12px;
    max-width: 98vw;
  }
  .open-btn, .close-btn {
    font-size: 1em;
    padding: 0.9em 0;
  }
}
</style>
