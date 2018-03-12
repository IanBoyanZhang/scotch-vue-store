<template>
  <div>
    <div class="products">
      <div class="container">
        <template v-for="product in products">
          <product-item :product="product"></product-item>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
  import ProductItem from './ProductItem.vue'
  export default {
    name: 'product-list',
    created () {
      if (this.products.length === 0) {
        // console.log(this.products.length)
        this.$store.dispatch('allProducts')
      }
    },
    computed: {
      // TODO: Use serialized product info
      // V2-> setting up back end for persistent storage
      products () {
        return this.$store.getters.allProducts
      }
    },
    data () {
      return {
      }
    },
    components: {
      'product-item': ProductItem
    }
  }
</script>

<style>
  .products {
    background: #F7F8FB;
    padding: 30px 0;
  }
</style>
