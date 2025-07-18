<template>
  <p class="hello-user" id="hello-user"><span class="user-name" v-bind="$attrs" id="hello-username">{{ name }}</span>!</p>
</template>

<script>
export default {
  props: ['name'] // Nhận prop 'name' từ component cha
}
</script>

<style scoped>
.hello-user {
  text-align: center;
  font-size: 1.35em;
  font-weight: 700;
  color: #38c6ff;
  margin: 1em 0 0.7em 0;
  letter-spacing: 0.5px;
}
.user-name {
  color: orange;
  font-weight: 800;
  font-size: 1.15em;
}
@media (max-width: 700px) {
  .hello-user {
    font-size: 1.1em;
    margin: 0.7em 0 0.5em 0;
  }
  .user-name {
    font-size: 1em;
  }
}
</style>
