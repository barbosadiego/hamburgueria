<template>
  <nav class="nav"> 
    <router-link to="/" id="logo">
      <img :src="logo" :alt="alt" >
    </router-link>
    <router-link to="/">Home</router-link>
    <router-link to="/pedidos">Pedidos</router-link>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  props: ["logo", "alt"]
}
</script>

<style scoped>
.nav{
  background-color: var(--bg-color);
  border-bottom: 4px solid #1111;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
#logo{
  margin: auto;
  margin-left: 0;
}
#logo img{
  height: 40px;
  width: 40px;
}
.nav a{
  color: var(--primary);
  text-decoration: none;
  margin: 12px;
  transition: .5s;
}
.nav a:hover{
  color: #fff;
}
</style>
