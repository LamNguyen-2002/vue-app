<template>
  <div class="box slot-box">
    <header class="slot-header"><slot name="header" /></header>
    <main class="slot-main"><slot /></main>
  </div>
</template>

<script>
export default {} // Component không có logic đặc biệt, chỉ dùng slot
</script>

<style scoped>
.slot-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: var(--color-background);
  border-radius: 18px;
  box-shadow: 0 2px 16px rgba(44, 62, 80, 0.09);
  padding: 1.2em 1em;
  margin: 1em 0;
  width: 100%;
  box-sizing: border-box;
}
.slot-header {
  width: 100%;
  text-align: center;
  font-size: 1.25em;
  font-weight: 800;
  color: #4f8cff;
  margin-bottom: 1em;
  letter-spacing: 0.5px;
}
.slot-main {
  width: 100%;
  text-align: center;
  font-size: 1.1em;
  color: #2c3e50;
  margin-bottom: 0.5em;
}
@media (max-width: 700px) {
  .slot-header {
    font-size: 1em;
    margin-bottom: 0.7em;
  }
  .slot-main {
    font-size: 1em;
    margin-bottom: 0.3em;
  }
  .slot-box {
    padding: 0.7em 0.2em;
    border-radius: 12px;
  }
}
</style>
