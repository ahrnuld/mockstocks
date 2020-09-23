<template>
  <tr>
    <td  class="is-vcentered">{{ name }}</td>
    <td class="is-vcentered" :class="{ down: price < previousPrice, up: price > previousPrice }">
      <b>{{ currency }} {{ formatPrice(price) }}</b>
    </td>
    <td><button class="button is-primary" @click="$emit('buy', name)">Buy</button></td>
  </tr>
</template>

<script>
export default {
  name: "stock",
  props: {
    name: String,
    price: Number,
    previousPrice: Number,
    currency: String,
  },
  methods: {
    formatPrice(value) {
      let val = (value / 1).toFixed(2).replace(".", ",");
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
  },
};
</script>

<style>
.down {
  color: maroon;
}
.up {
  color: darkgreen;
}
</style>