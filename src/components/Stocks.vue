<template>
  <div>
    <table class="table">
      <thead>
        <td>Name</td>
        <td>Price</td>
                <td>Actions</td>
      </thead>
      <tbody>
        <stock v-for="stock in stocks" :key="stock.name" :name="stock.name" :price="stock.price" 
        :previousPrice="stock.previousPrice" :currency="stock.currency" @buy="buyStock" />
      </tbody>
    </table>
  </div>
</template>

<script>
import stock from './Stocks/Stock.vue';

export default {
  name: "stocks",
  components: { stock },
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
    buyStock(name)
    {
      alert(name);
    }   
  },
  mounted() {
    setInterval(() => {
      this.updatePrices();
    }, 1000);
  },
};
</script>

<style>

</style>