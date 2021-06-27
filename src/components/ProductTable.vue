<template>
<div>
    <label >
        Product:
        <input type="text" v-model="searchProduct">
    </label>
    <table border="2px">
        <tr>
            <th>Title</th>
            <th>Price</th>
            <th>Options</th>
        </tr>
        <tr v-for="product in filteredProducts" :key="product.id">
            <td :class="getProductClass(product)" >
                {{product.title}}</td>
            <td>{{product.price}}</td>
            <td>
                <span v-if="product.price<=userMoney"><button>Купити</button> </span>
                <span v-else>Не вистачає: {{userMoney-product.price}} </span>
                <!-- <span v-show="product.price<=userMoney"><button>Купити</button> </span> -->
                <!-- <span v-else> {{`Не вистачає: ${userMoney-product.price}`}} </span> -->
            </td>
        </tr>
    </table>
    </div>
</template>
<script>
    export default {
        name:'ProductTable',
        props: {
            userMoney: {
                type: Number,
                default: 0
            },
            products: {
                type: Array,
                default: ()=>[]
            },
        },
        data() {
            return {
                searchProduct: null,  //Змінна де зберігаємо назву товару, що шукаємо
                filteredProducts:this.products
            }
        },
        watch: {  //Розділ, у якому записуємо змінні, зміну яких відслідковуємо
            searchProduct(newValue) { //Функція, яка буде викликатися коли значення "searchProduct" буде змінено
                        // "newValue" - нове значення змінної "searchProduct"
                const val=newValue.toLowerCase()
                this.filteredProducts=this.products.filter(product=>product.title.toLowerCase().startsWith(val))
            }
        },
        methods: {
            getProductClass(product) {
                return product.price<=this.userMoney?'can-buy':'can-not-buy' 
            }
        },
    }
</script>
<style lang="css" scoped>
.can-buy{
    color:green
}
.can-not-buy{
    color:red
}
</style>