<template>
  <tr>
       <td>{{stock.name}}</td>
         <td>{{ formatPrice(stock.priceBought)}}</td>
          <td>{{stock.amount}}</td>
          <td>{{ formatPrice(stock.amount * stock.priceBought) }}</td>  
        </tr>
</template>

<script>
export default {
    name: 'PortfolioItem',
    props: {
        stock: Object
    }
}
</script>

<style>

</style>