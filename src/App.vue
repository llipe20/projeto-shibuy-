<template>
  <Nav :logo="logo_scr" :nome="alt"/>
  <router-view/>
  <Footer />
</template>

<script>
import Nav from "./components/Nav.vue"
import Footer from "./components/Footer.vue"

export default {
  name :  'App',

  components : {
    Nav, Footer
  },

  data() {
    return {
      logo_scr : "/img/logo.png",
      nome : "img-logo"
    }
  }
}
</script>

<style>
* {
  font-family: Arial, Helvetica, sans-serif;
  box-sizing: border-box;
  overflow-x: hidden;
  padding: 0;
  margin: 0;
}

html::-webkit-scrollbar {
    display: none;
}

.box-main {
  padding: 50px;
  height: auto;
  min-height: 74vh;
}

h1 {
  text-align: center;
  margin-bottom: 30px;
  font-size: 2em;
  counter-reset: black;
}
</style>

