<template>
  <div id="app">
    <product-card
    :user-money="1000"
    :products="dataProductsList"
    />
    <br>
    <age-solver-n :user-age="age"/>
    <label>
      Введіть вік користувача
      <input type="number" v-model="age">
    </label>
    <br>
    <product-table
     :user-money="5000"
     :products="dataProductsList"/>
  </div>
</template>

<script>
import ProductCard from './components/ProductCard.vue'
import AgeSolverN from './components/AgeSolverN.vue'
import ProductTable from './components/ProductTable.vue'

export default {
  name: 'App',
  components: {
    ProductCard,
    AgeSolverN,
    ProductTable
  },
  data() {
    return {
    age: 21,
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
    ],
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
