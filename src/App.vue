<template>
  <div id="app">
    <section class="section">
    <div class="container">
      <h1 class="title">Mock stocks</h1>
    <Stocks/>
       </div>
  </section>
  </div>
</template>

<script>
import Stocks from './components/Stocks.vue'

export default {
  name: 'App',
  components: {
    Stocks
  }
}
</script>

<style>
#app {

}
</style>
