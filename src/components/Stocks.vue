<template>
  <div>
    <table class="table">
      <thead>
        <td>Name</td>
        <td>Price</td>
      </thead>
      <tbody>
        <tr v-for="stock in stocks" :key="stock.name">
          <td>{{stock.name}}</td>
          <td
            :class="{'down': stock.price < stock.previousPrice, 'up': stock.price > stock.previousPrice}"
          >
            <b>{{stock.currency}} {{formatPrice(stock.price)}}</b>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "stocks",
  data() {
    return {
      stocks: [
        { name: "BMW", price: 61.05, previousPrice: 0, currency: "€" },
        { name: "Caterpillar", price: 146.49, previousPrice: 0, currency: "$" },
        { name: "AMD", price: 76.5, previousPrice: 0, currency: "$" },
        { name: "Gazprom", price: 4.583, previousPrice: 0, currency: "$" },
      ],
    };
  },
  methods: {
    updatePrices() {
      this.stocks.forEach((stock) => {
        stock.previousPrice = stock.price;
        let random = (Math.random() - 0.5) * 2;
        stock.price += random;
        if (stock.price < 0) {
          stock.price = 0;
        }
      });
    },
    formatPrice(value) {
      let val = (value / 1).toFixed(2).replace(".", ",");
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
  },
  mounted() {
    setInterval(() => {
      this.updatePrices();
    }, 1000);
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