<template>
  <div v-if="show" class="full-product-card">
    <div class="image">
      <img :src=product.image height="300">
    </div>
    <div class="text">
      <p><strong>Name: </strong>{{product.title}}</p>
      <p><strong>Category: </strong>{{product.category}}</p>
      <p><strong>Description: </strong>{{product.description}}</p>
      <p><strong>Rating: </strong>{{product.rating.rate}}/5 ({{product.rating.count}} rewievs)</p>
    </div>
    <div class="price-back">
      <p><strong>Price: </strong>{{product.price}}$</p>
      <img src="@/assets/back.png" @click="$event => show = false" width="50" height="50" class="back">
    </div>
  </div>
</template>

<script>
export default {
  name: "FullProductCard",
  props: {
    product: Object,
    show: Boolean
  }
}
</script>

<style scoped>
  .full-product-card{
    width: 600px;
    height: 600px;
    background: #E7FFD4;
    position: fixed;
    left: 650px;
    top: 120px;
  }
  .image{
    height: 300px;
    width: 600px;
    background: #FFFFFF;
    text-align: center;
  }
  .price-back{
    display: flex;
  }
  .back{
    position: absolute;
    right: 10px;
    bottom: 10px;

  }
</style>