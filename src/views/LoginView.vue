<template>
  <div class="login">
    <button class="login-btn" @click="login">LOGIN</button>
  </div>
</template>

<script>
export default {
  name: 'LoginView',
  methods: {
    login() {
      localStorage.setItem('loginID', 'asdfg1234')
      this.$router.push({ name: 'shop' })
    }
  }
}
</script>

<style scoped>
.login-btn {
  background-color: #ff0000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.login-btn:hover {
  background-color: #f81414;
}
</style>
