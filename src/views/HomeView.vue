<template>
  <Banner :banner="scr_banner"/>

  <div class="box-main">
    <h1>Monte seu burger:</h1>
    <Form />
  </div>
</template>

<script>
import Banner from '../components/Banner.vue'
import Form from '../components/Form.vue'

export default {
  name : 'Home',

  components : {
    Banner, Form
  },

  data() {
    return {
      scr_banner : "background-image: url('../img/burger.jpg')"
    }
  }
}
</script>

<style scoped>
  
</style>