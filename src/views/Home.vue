<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>Create New Product</h2>
    <button v-on:click="createProduct()">Create</button>

    <div v-for="product in products">
      <h2>{{ product.name }}</h2>
      <img v-bind:src="product.image_url" alt />
      <p>Price: {{ product.price }}</p>
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
      message: "Random Stuff that Peter Owns that He Wants to Sell to You!",
      products: []
    };
  },
  created: function() {
    axios.get("/api/products").then(response => {
      this.products = response.data;
    });
  },
  methods: {
    createProduct: function() {
      var params = {
        name: "Hockey Puck",
        description: "Best hockey puck I could find.",
        price: 100,
        image_url:
          "https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSVcoKk3tccQHe1az-ZiMQ8eqOu00GbNMSD-I1YHsquS2y7-oroPvF36Ws7vpUbxL-OABJt6VGQ&usqp=CAc"
      };
      axios.post("/api/products", params).then(response => {
        console.log("Success!", response.data);
        this.products.push(response.data);
      });
    }
  }
};
</script>
