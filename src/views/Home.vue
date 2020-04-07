<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>Create New Product</h2>
    <div>
      <div>
        Name:
        <input type="text" v-model="newProductName" />
      </div>
      <div></div>
      <div>
        Description:
        <input type="text" v-model="newProductDescription" />
      </div>
      <div>
        Price:
        <input type="text" v-model="newProductPrice" />
      </div>
      <div>
        Image URL:
        <input type="text" v-model="newProductImageUrl" />
      </div>
    </div>
    <button v-on:click="createProduct()">Create</button>

    <div v-for="product in products">
      <h2>{{ product.name }}</h2>
      <img v-bind:src="product.image_url" alt />
      <div v-if="false">
        <p>Price: {{ product.price }}</p>
        <p>Description: {{ product.description }}</p>
      </div>
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
      message: "You just lost the game!",
      products: [],
      newProductName: "",
      newProductDescription: "",
      newProductPrice: "",
      newProductImageUrl: ""
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
        name: this.newProductName,
        description: this.newProductDescription,
        price: this.newProductPrice,
        image_url: this.newProductImageUrl
      };
      axios.post("/api/products", params).then(response => {
        console.log("Success!", response.data);
        this.products.push(response.data);
      });
    }
  }
};
</script>
