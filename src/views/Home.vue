<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="product in products">
      <h2>Product: {{ product.name }}</h2>
      <img v-bind:src="product.image_url" alt />
      <h3>Price: {{ product.price }}</h3>
      <p>Description: {{ product.description }}</p>
    </div>
  </div>
</template>

<style>
img {
  width: 300px;
}
</style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      products: []
    };
  },
  created: function() {
    axios.get("/api/products").then(response => {
      this.products = response.data;
    });
  },
  methods: {}
};
</script>
