<template>
  <tr>
 <td>{{stock.name}}</td>
          <td
            :class="{'down': stock.price < stock.previousPrice, 'up': stock.price > stock.previousPrice}"
          >
          <b>{{stock.currency}} {{formatPrice(stock.price)}}</b>
          </td>
          <td><input type="text" v-model="amount" class="input"></td>
          <td><button class="button" @click="$emit('buy', stock.name, amount)">Buy</button></td>
  </tr>
</template>

<script>
export default {
  name: "StockItem",
  data() {
      return {
          amount: 0
      }
  },
  props: {
    // name: String,
    // price: Number,
    // previousPrice: Number,
    // currency: String,
    stock: Object
  },
};
</script>

<style>
</style>