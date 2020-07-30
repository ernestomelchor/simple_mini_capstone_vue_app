<template>
  <div class="home">
    <h1 class="mb-5">{{ message }}</h1>
    <ul>
      <li
        class="errors alert alert-danger"
        role="alert"
        v-for="error in errors"
        v-bind:key="error.id"
      >{{ error }}</li>
    </ul>
    <h2 class="mb-3">Create New Product</h2>
    <div class="mb-3">
      <div class="mb-3">
        Name:
        <input type="text" v-model="newProductName" />
      </div>
      <div class="mb-3">
        Description:
        <input type="text" v-model="newProductDescription" />
      </div>
      <div class="mb-3">
        Price:
        <input type="text" v-model="newProductPrice" />
      </div>
      <div class="mb-3">
        Image URL:
        <input type="text" v-model="newProductImageUrl" />
      </div>
    </div>
    <button class="btn btn-primary mb-5" type="submit" v-on:click="createProduct()">Create</button>

    <div class="mb-5" v-for="product in products" v-bind:key="product.id">
      <h2 class="mb-3">{{ product.name }}</h2>
      <img class="mb-3" v-bind:src="product.image_url" alt />
      <div>
        <button class="btn btn-info" v-on:click="showProduct(product)">Show more info</button>
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
          <button
            type="button"
            class="btn btn-primary btn-sm"
            v-on:click="updateProduct(product)"
          >Update</button>
        </div>
        <br />
        <div>
          <button
            class="btn btn-primary"
            type="submit"
            v-on:click="deleteProduct(product)"
          >Delete This Product</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style></style>

<script>
var axios = require("axios");
var bootstrap = require("bootstrap");

export default {
  data: function () {
    return {
      message: "Buy Me a Coffee!",
      errors: [],
      products: [],
      currentProduct: {},
      newProductName: "",
      newProductDescription: "",
      newProductPrice: "",
      newProductImageUrl: "",
    };
  },
  created: function () {
    axios.get("/api/products").then((response) => {
      this.products = response.data;
    });
  },
  methods: {
    createProduct: function () {
      var params = {
        name: this.newProductName,
        description: this.newProductDescription,
        price: this.newProductPrice,
        image_url: this.newProductImageUrl,
      };
      axios
        .post("/api/products", params)
        .then((response) => {
          console.log("Success!", response.data);
          this.products.push(response.data);
          this.newProductName = "";
          this.newProductDescription = "";
          this.newProductPrice = "";
          this.newProductImageUrl = "";
        })
        .catch((error) => {
          console.log(error.response.data.errors);
          this.errors = error.response.data.errors;
        });
    },
    showProduct: function (product) {
      if (this.currentProduct === product) {
        this.currentProduct = {};
      } else {
        this.currentProduct = product;
      }
    },
    updateProduct: function (product) {
      var params = {
        name: product.name,
        description: product.description,
        price: product.price,
        image_url: product.image_url,
      };
      axios.patch("/api/products/" + product.id, params).then((response) => {
        console.log("Success!", response.data);
      });
    },
    deleteProduct: function (product) {
      console.log("Delete product...", product.name);
      axios.delete("/api/products/" + product.id).then((response) => {
        console.log("Success!");
        var index = this.products.indexOf(product);
        this.products.splice(index, 1);
      });
    },
  },
};
</script>
