<template>
  <div>
    <table class="table">
      <thead>
        <td>Name</td>
        <td>Price</td>
        <td></td>
        <td></td>
      </thead>
      <tbody>
        <stock-item
          v-for="stock in stocks"
          :key="stock.name"
          :stock="stock"
          @buy="buyStock"
        />
      </tbody>
    </table>
    <h1 class="title">Stock portfolio</h1>
    <table class="table">
      <thead>
        <td>Name</td>
        <td>Buy price</td>
        <td>Amount</td>
        <td>Total value</td>
      </thead>
      <tbody>
        <portfolio-item v-for="stock in portfolio" :key="stock.name"
        :stock="stock" />
      </tbody>
    </table>
  </div>
</template>

<script>
import StockItem from "./StockItem.vue";
import PortfolioItem from "./PortfolioItem.vue"

export default {
  components: {
    StockItem,
    PortfolioItem
  },
  name: "stocks",
  data() {
    return {
      stocks: [
        { name: "BMW", price: 61.05, previousPrice: 0, currency: "€" },
        { name: "Caterpillar", price: 146.49, previousPrice: 0, currency: "$" },
        { name: "AMD", price: 76.5, previousPrice: 0, currency: "$" },
        { name: "Gazprom", price: 4.583, previousPrice: 0, currency: "$" },
      ],
      portfolio: [],
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
    buyStock(stockToBuy, amount) {
      let chosenStock = this.stocks.find((s) => s.name == stockToBuy);
      this.portfolio.push({
        name: chosenStock.name,
        priceBought: chosenStock.price,
        amount: amount,
      });
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