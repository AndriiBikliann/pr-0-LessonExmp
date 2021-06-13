<template>
    <div>
       <label>
           Product:
           <input type="text" v-model="searchProduct">
       </label>

       <label>
           Price:
           <input type="number" v-model="searchPrice">
       </label>

       <table border="2px">
           <tr>
               <th>Title</th>
               <th>Price</th>
               <th>Options</th>
           </tr>
           <tr v-for="product in filteredProducts" :key="product.id">
             <td :class = "getProductClass"> {{product.title}}</td>
             <td> {{product.price}} </td>
             <td>
                 <span v-if="product.price<=userMoney"> <button>Купити</button></span>
                 <span v-else>Не вистачає: {{userMoney-product.price}}</span>
             </td>
           </tr>
       </table>

    </div>
</template>

<script>
    export default {
        name: 'ProductCard',
        props: {
            userMoney: {
                type: Number,
                default: 0
            },
            products: {
                type: Array,
                default: ()=>[]
            }
        },
        data() {
            return {
                searchProduct: null,
                filteredProducts: this.products,
                searchPrice: null
            }
        },
        watch: {
            searchProduct() {
                this.filteredProducts()
            },
            searchPrice(){
                this.filteredProducts()
            }
        },
        methods: {
            getProductClass(product) {
                return product.price<=this.userMoney? 'can-buy': 'can-not-buy'
            },
            filterProducts() {
                const val=this.searchProduct.toLowerCase()

                this.filteredProducts=this.products.filter(product=>(
                  (!val || product.title.toLowerCase().startsWith(val)) &&
                  (!this.searchPrice || product.price<=parseFloat(this.searchPrice))  
                ))
            }
        },
    }
</script>

<style lang="css" scoped>
.can-buy {
    color: green
}
.can-not-buy {
    color: red;
}
</style>