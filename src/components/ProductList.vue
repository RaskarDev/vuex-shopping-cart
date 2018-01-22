<template>
  <div>
    <h1>Product List</h1>
    <img src="https://i.imgur.com/JfPpwOA.gif" v-if="loading" alt="">
    <ul v-else>
      <li v-for="product in products">{{product.title}} - {{product.price}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading: false
    };
  },
  computed: {
    products() {
      return this.$store.getters.availableProducts;
    }
  },

  created() {
    this.loading = true;
    this.$store.dispatch('fetchProducts').then(() => (this.loading = false));
  }
};
</script>

<style>

</style>
