<template>
  <div class="">
    <Navbar />
    <div class="container">
      <div class="row mt-4">
        <div class="">
          <h1>Daftar <strong> Makanan</strong></h1>
        </div>
      </div>
      <div class="row mt-3">
        <div class="col">
          <div class="input-group mb-3">
            
            <input
              type="text"
              class="form-control"
              placeholder="Cari Makanan kesukaan anda.."
              aria-label="Cari"
              aria-describedby="basic-addon1"
            />
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">
                <b-icon-search></b-icon-search>
              </span>
            </div>
          </div>
        </div>
      </div>
      <div class="row mb-4">
        <div
          class="col-md-4 mt-4"
          v-for="product in products"
          :key="product.id"
        >
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
  name: "Foods",
  components: {
    Navbar,
    CardProduct,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/products")
      .then((response) =>
        // handle success
        this.setProducts(response.data)
      )
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>