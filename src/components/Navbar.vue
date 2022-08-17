<template>
  <nav>
    <router-link to="/">
      <img :src="img" id="logo">
    </router-link>
    <router-link to="/">Home</router-link> |
    <router-link to="/pedidos">Pedidos</router-link>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  props: ["img"]
}
</script>

<style scoped></style>
