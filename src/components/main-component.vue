<template>
  <div class="productItem" v-if="product">
    <div class="productInfo">
      <img class="productInfoImage" :src="product.thumbnail" alt="">
      <div class="productInfoDescription">
        <p>Price: {{ product.price }}</p>
        <p>Discount: {{ product.discountPercentage }}</p>
        <p>Rating: {{ product.rating }}</p>
        <p>Stock: {{ product.stock }}</p>
      </div>
    </div>

    <div class="divider"></div>

    <div class="productDescription">
      <h2>{{ product.title }}</h2>  
      <div>{{ product.description }}</div>
    </div>
  </div>

  <div v-else>
    Please select product
  </div>
</template>

<script>

export default {
  name: "MainComponent",
  props: {
    product: {
      id: String,
      name: String,
      token: String,
    },
    loading: Boolean
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .productItem {
    padding-right: 24px;
    padding-left: 24px;
  }
  .productInfo {
    display: flex;
    padding-top: 24px;
  }
  .productInfoImage {
    width: 30%;
  }
  .divider {
    width: 100%;
    height: 1px;
    background: rgba(140, 140, 140, 0.35);
    margin-top: 24px;
    margin-bottom: 24px;
  }
  .productInfoDescription {
    width: 70%; 
    padding-right: 24px;
    padding-left: 24px;
  }
</style>
