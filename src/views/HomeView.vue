<template>
  <section >
    <Banner />
    <div class="main-container">
      <h1>Monte o seu burguer:</h1>
      <p>formulário</p>
    </div>
  </section>
</template>

<script>
import Banner from '@/components/Banner.vue';

export default {
  name: 'HomeView',
  components: {
    Banner,
  },
};
</script>
