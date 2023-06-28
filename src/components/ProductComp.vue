<template>
  <div class="products" id="products">
    <div v-for="product in products" :key="product.id">
      <div class="card text-center" style="width: 100%;">
        <img :src="product.image" class="card-img-top" alt="Product Image" loading="lazy">
        <div class="card-body">
          <h5 class="card-title text-center">{{ product.name }}</h5>
          <p class="card-text text-center">Price: R{{ product.price }}</p>
          <button class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#checkoutModal" @click="addToCart(product)">Add to Cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [],
    };
  },
  async created() {
    try {
      const response = await fetch("https://aphelele2.github.io/jsonVue/products.json");
      this.products = await response.json();
    } catch (error) {
      console.error("Error fetching products:", error);
    }
  },
  methods: {
    addToCart(product) {
      // Add your logic here to add the product to the cart
      console.log("Adding to cart:", product);
    },
  },
};
</script>

<style scoped>

</style>
