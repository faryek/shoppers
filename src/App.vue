<template>
  <div v-show="main"><MainPage @toGeneral="main = true; cart = false" @toCart="main = false; cart = true"></MainPage></div>
  <div v-show="cart"><ShoppingCartPage @toGeneral="main = true; cart = false" @toCart="main = false; cart = true"></ShoppingCartPage></div>
</template>

<script>
import MainPage from './components/MainPage.vue'
import ShoppingCartPage from './components/ShoppingCartPage.vue'
export default {
  name: 'App',
  components: {
    MainPage,
    ShoppingCartPage
  },
  data () {
    return {
      main: true,
      cart: false
    }
  },
  mounted () {
    console.log(this.main)
    console.log(this.cart)
  }
}
</script>
<style>
</style>
