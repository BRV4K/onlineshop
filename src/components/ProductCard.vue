<template>
  <div class="product-card">
    <img :src=product.image class="image" @click="showTrue" >
    <p class="title">{{product.title}}</p>
    <div class="price-basket">
      <p class="price">{{product.price}}$</p>
      <img src="@/assets/basket.png" width="50" height="50">
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    product: Object,
    show: Boolean,
  },
  methods: {
    addProduct(){
      this.$emit('addProduct')
    },
    showTrue(){
      this.$emit('showTrue')
    }
  }
}
</script>

<style scoped>
  .product-card{
    width: 300px;
    height: 300px;
    background: #FFFFFF;
    text-align: center;
  }
  .image{
    height: 170px;
    width: auto;
    max-width: 300px;
  }
  .price-basket{
    display: flex;
    align-items: center;
  }
  .price{
    margin-left: 50px;
    margin-right: 50px;
    font-weight: 700;
    font-size: 20px;
    line-height: 24px;
  }
  .title{
    font-weight: 400;
    font-size: 17px;
    line-height: 20px;
  }
</style>