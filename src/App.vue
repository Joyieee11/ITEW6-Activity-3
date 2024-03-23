<template>
  <nav>
    <router-link to="/login">Login</router-link> |
    <router-link to="/shop">Shop</router-link>
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #000000; 
  text-decoration: none; 
  transition: color 0.3s; 
}

nav a:hover {
  color: #000000; 
}

nav a.router-link-exact-active {
  color: #ff0000; 
}
</style>
