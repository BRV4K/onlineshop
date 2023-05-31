<template>
  <link href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;700;800&display=swap" rel="stylesheet">
  <div class="app">
    <header>
      <h1>Online shop</h1>
      <img class='image' src="@/assets/basket.png" alt="Basket" @click="$event => showBasket = true">
    </header>

    <main>
      <basket :show-basket="showBasket" :basket="basket"></basket>
      <div class="input">
        <div class="search-type-img">
          <input type="text" v-model='search' placeholder="Search" class="input-type">
          <img src="@/assets/search.png" width="50" height="50" class="serach-img" @click="find">
        </div>
        <select class="sort">
          <option value="price">Price</option>
          <option value="alphabet">Alphabet</option>
        </select>
      </div>
      <div class="products">
        <productCard v-for="product in products" :key="product.id" :product="product" :show="show" @addProduct="addProduct" @showTrue="showTrue"/>
      </div>
      <fullProductCard v-for="product in products" :key="product.id" :product="product" :show="show"/>
    </main>
  </div>
</template>

<script>
import productCard from "@/components/ProductCard";
import fullProductCard from "@/components/FullProductCard";
import axios from 'axios';
import basket from "@/components/Basket";
import Basket from "@/components/Basket";

export default {
  components:{
    Basket,
    fullProductCard,
    productCard
  },
  data(){
    return {
      products: this.products,
      show: false,
      showBasket: true,
      basket: [],
      search: ''
    }
  },
  methods:{
    async getProducts() {
      try {
        const responce = await axios.get('https://fakestoreapi.com/products');
        if (responce.status === 200) {
          this.products = responce.data;
          console.log(this.products)
        }
      }
      catch(e) {
        console.error(e);
      }
    },

    addProduct(product){
      this.basket.push({id: product.id, title: product.title, price: product.price})
      console.log(basket)
    },
    showTrue(){
      this.show = true;
    }
  },
  mounted() {
    this.getProducts();
  }

}
</script>

<style>
  * {
    font-family: Raleway;
    margin: 0;
    padding: 0;
  }
  header{
    background: #FFFFFF;
    height: 102px;
    text-align: center;
    display: flex;
    gap: 479px;
  }
  h1{
    font-weight: 800;
    font-size: 60px;
    line-height: 72px;
    margin-left: 791px;
    margin-top: 15px;
  }
  .image{
    height: 102px;
    width: 102px;
  }
  main{
    background: #E7FFD4;
    padding-top: 20px;
  }
  .products{
    margin-left: 210px;
    margin-right: 210px;
    display: grid;
    grid-template-columns: 300px 300px 300px 300px;
    grid-column-gap: 100px;
    grid-row-gap: 50px;
    padding-bottom: 100px;
  }
  .input{
    margin-left: 210px;
    margin-bottom: 50px;
    position: relative;
    display: flex;
  }
  .input-type{
    font-size: 30px;
    border: none;
    width: 300px;
    height: 53px;
    border-radius: 30px;
    text-align: center;
    margin-right: 25px;
  }
  .sort{
    font-size: 30px;
    border: none;
    width: 300px;
    height: 53px;
    border-radius: 30px;
    text-align: center;
    position: absolute;
    left: 1200px;
  }
  .serach-img{
    position: absolute;
    bottom: 0;
  }
  .search-type-img{
    position: relative;
  }
</style>