<template>
  <ul class="user-list" id="user-list">
    <li v-for="(user, index) in users" :key="index" class="user-list-item" :id="`user-list-item-${index}`">
      <span class="user-index">👤 {{ index + 1 }}.</span> <span class="user-name">{{ user }}</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: ['users'] // Nhận prop 'users' là mảng tên người dùng từ component cha
}
</script>

<style scoped>
.user-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0;
  width: 100%;
}
.user-list-item {
  display: flex;
  align-items: center;
  gap: 1em;
  width: 100%;
  max-width: 350px;
  font-size: 1.15em;
  background: var(--color-background-mute);
  border-radius: 12px;
  box-shadow: 0 1px 6px rgba(44, 62, 80, 0.06);
  margin-bottom: 0.7em;
  padding: 1em 1.2em;
  transition: background 0.2s, box-shadow 0.2s;
}
.user-list-item:hover {
  background: #e6f0ff;
  box-shadow: 0 2px 12px rgba(44, 62, 80, 0.13);
}
.user-index {
  color: #38c6ff;
  font-weight: 800;
  min-width: 2.5em;
  text-align: right;
  font-size: 1.1em;
}
.user-name {
  color: #2c3e50;
  font-weight: 600;
  font-size: 1.1em;
}
@media (max-width: 700px) {
  .user-list-item {
    font-size: 1em;
    padding: 0.9em 0.7em;
    max-width: 100%;
  }
  .user-index, .user-name {
    font-size: 1em;
  }
}
</style>
