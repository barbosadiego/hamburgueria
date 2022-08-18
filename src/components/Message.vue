<template>
  <div v-if="msg" class="message-container">
    <p>{{ msg }}</p>
  </div>
</template>

<script>
export default {
  name: 'Message',
  props:{
    msg: String,
  }
}
</script>

<style scoped>
.message-container{
  color: #004085;
  background-color: #cce5ff;
  border: 2px solid #b8daff;
  border-radius: 5px;
  max-width: 400px;
  margin: 20px auto;
  text-align: center;
}
</style> 