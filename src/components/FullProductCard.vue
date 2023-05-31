<template>
  <div v-if="show" class="full-product-card">
    <div class="image">
      <img :src=product.image>
    </div>
    <div class="text">
      <p><strong>Name: </strong>{{product.title}}</p>
      <p><strong>Category: </strong>{{product.category}}</p>
      <p><strong>Description: </strong>{{product.description}}</p>
      <p><strong>Rating: </strong>{{product.rating.rate}}/5 ({{product.rating.count}} rewievs)</p>
    </div>
    <div>
      <p><strong>Price: </strong>{{product.price}}$</p>
      <img src="@/assets/back.png" @click="$event => show = false">
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
    background: #FFFFFF;
  }
  .image{
    width: 600px;
    background: #FFFFFF;
  }
</style>