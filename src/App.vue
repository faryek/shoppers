<template>
  <MainPage v-show="main" @toGeneral="main = true; cart = false" @toCart="main = false; cart = true"></MainPage>
  <ShoppingCartPage v-show="cart" @toGeneral="main = true; cart = false" @toCart="main = false; cart = true"></ShoppingCartPage>
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
  }
}
</script>
<style>
</style>
