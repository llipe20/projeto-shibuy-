<template>
  <div class="box-main">
    <h1>PEDIDOS</h1>

    <Dashboard />
  </div>
</template>

<script>
import Dashboard from '../components/Dashboard.vue'
export default {
    name : 'Pedidos',

    components : {
      Dashboard
    },

    data() {
      return {

      }
    }
}
</script>
