<template>
  <div class="basket" v-if="showBasket">
    <p>Your products: </p>
    <div v-for="product in basket" :key="product.id">{{product.title}}</div>
    <div>
      <p><strong>Total price: </strong></p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Basket",
  props: {
    basket: Array,
    showBasket: Boolean
  }
}
</script>

<style scoped>
  .basket{
    width: 300px;
    position: fixed;
    right: 0;
    top: 120px;
  }
</style>