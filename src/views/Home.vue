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
      <div>
        <button v-on:click="showProduct(product)">Show more info</button>
      </div>
      <div v-if="product === currentProduct">
        <p>Price: {{ product.price }}</p>
        <p>Description: {{ product.description }}</p>
        <div>
          <h4>Update Product</h4>
          <div>
            <div>
              Name:
              <input type="text" v-model="product.name" />
            </div>
            <div></div>
            <div>
              Description:
              <input type="text" v-model="product.description" />
            </div>
            <div>
              Price:
              <input type="text" v-model="product.price" />
            </div>
            <div>
              Image URL:
              <input type="text" v-model="product.image_url" />
            </div>
          </div>
          <button v-on:click="updateProduct(product)">Update</button>
        </div>
        <br />
        <div>
          <button v-on:click="deleteProduct(product)">Delete This Product</button>
        </div>
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
      currentProduct: {},
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
    },
    showProduct: function(product) {
      if (this.currentProduct === product) {
        this.currentProduct = {};
      } else {
        this.currentProduct = product;
      }
    },
    updateProduct: function(product) {
      var params = {
        name: product.name,
        description: product.description,
        price: product.price,
        image_url: product.image_url
      };
      axios.patch("/api/products/" + product.id, params).then(response => {
        console.log("Success!", response.data);
      });
    },
    deleteProduct: function(product) {
      console.log("Delete product...", product.name);
      axios.delete("/api/products/" + product.id).then(response => {
        console.log("Success!");
        var index = this.products.indexOf(product);
        this.products.splice(index, 1);
      });
    }
  }
};
</script>
