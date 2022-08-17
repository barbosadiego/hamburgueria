<template>
  <div id="app">
    <Navbar :logo="logo_src" :alt="alt" />
    <main>
      <router-view />
    </main>
    <Footer />
  </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue';
import Footer from '@/components/Footer.vue';

export default {
  components: {
    Navbar,
    Footer,
  },
  data() {
    return {
      logo_src: '/img/logo.png',
      alt: 'Make Your Burguer',
    };
  },
};
</script>

<style>
:root {
  --primary: #fcba03;
  --text: #222;
  --bg-color: #222;
}
* {
  box-sizing: border-box;
}
body {
  margin: 0px;
  padding: 0px;
  font-family: Arial, Helvetica, sans-serif;
}
#app{
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%;
}
main{
  flex: 1;
}
.main-container{
  margin: 50px;
}
h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: var(--text);
}
</style>
