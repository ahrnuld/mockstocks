<template>
  <div id="app">
    <section class="section">
    <div class="container">
      <h1 class="title">Mock stocks</h1>
      <stocks/>
       </div>
  </section>
  </div>
</template>

<script>
import stocks from './components/Stocks.vue'

export default {
  name: 'App',
  components: {
    stocks
  }
}
</script>

<style>
#app {

}
</style>
