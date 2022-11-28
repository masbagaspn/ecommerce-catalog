<template>
  <main class="main" :class="containerBackground">
    <ProductSkeleton v-if="loading" />
    <ProductUnavailable 
      v-if="!isAvailable && !loading" 
      @increase-index="increaseIndex"
    />
    <ProductAvailable 
      v-if="isAvailable && !loading" 
      :details="product"
      @increase-index="increaseIndex"
    />
  </main>
</template>

<script>
import ProductAvailable from './components/ProductAvailable.vue'
import ProductSkeleton from './components/ProductSkeleton.vue'
import ProductUnavailable from './components/ProductUnavailable.vue'

export default {
  name: 'App',
  components: {
    ProductSkeleton,
    ProductAvailable,
    ProductUnavailable
},
  data() {
    return {
      loading: true,
      index: 1,
      product: Object
    }
  },
  mounted(){
    this.fetchProductByIndex(this.index)
  },
  watch: {
    index(newIndex, oldIndex) {
      if(newIndex !== oldIndex){
        this.fetchProductByIndex(newIndex)
      }
    }
  },
  computed: {
    checkIndex() {
      return this.index < 20
    },
    containerBackground() {
      return this.product.category === "men's clothing" ? 'main-men' : this.product.category === "women's clothing" ? 'main-women' : 'main-unavailable'
    },
    isAvailable() {
      return this.product.category === "men's clothing" || this.product.category === "women's clothing"
    }
  },
  methods: {
    async fetchProductByIndex(index) {
      this.loading = true;
      try{
        const response = await fetch(`https://fakestoreapi.com/products/${index}`);
        this.product = await response.json();
      } catch(err){
        console.error(err)
      } finally{
        this.loading = false;
      }
    },
    increaseIndex(){
      this.checkIndex ? this.index++ : this.index = 1
    }
  },
}
</script>

<style>
  @import './assets/style/app.css'
</style>
