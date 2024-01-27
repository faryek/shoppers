<template>
  <div v-show="main"><MainPage @toGeneral="main = true; cart = false" @toCart="main = false; cart = true" @add="count"></MainPage></div>
  <div v-show="cart"><ShoppingCartPage @toGeneral="main = true; cart = false" @toCart="main = false; cart = true" :items="currentItems"></ShoppingCartPage></div>
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
      cart: false,
      sel_card: {},
      currentItems: []
    }
  },
  methods: {
    count (a, card) {
      this.sel_card = card
      this.sel_card.counter = a
      console.log(a)
      this.addItem()
    },
    addItem () {
      if (!this.sel_card) {
        return
      }
      this.currentItems.push(this.sel_card)
      this.sel_card = {}
      this.saveItems()
      console.log(this.currentItems)
    },
    saveItems () {
      const parsed = JSON.stringify(this.currentItems)
      localStorage.setItem('items', parsed)
      console.log(this.currentItems)
    }
  },
  mounted () {
    console.log(this.main)
    console.log(this.cart)
    console.log(this.counter)
    console.log(this.sel_card)
  }
}
</script>
<style>
</style>
