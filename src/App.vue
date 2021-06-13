<template>
  <div id="app">
    <example-login/>
    <product-card
    :user-money="1000"
    :products="dataProductsList"
    />
  </div>
</template>

<script>
import ExampleLogin from './components/ExampleLogin.vue'
import ProductCard from './components/ProductCard.vue'

export default {
  name: 'App',
  components: {
    ExampleLogin,
    ProductCard
  },
  data() {
    return {
    dataProductsList: [
      {
        id:1,
        title:"TV",
        price:2000
      },
      {
        id:2,
        title:"Fridge",
        price:12000
      },
      {
        id:3,
        title:"TV2",
        price:10000
      },
    ]
  }
 }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
