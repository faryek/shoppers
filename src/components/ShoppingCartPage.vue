<template>
  <HeaderBlock @toGeneral="$emit('toGeneral')" @toCart="$emit('toCart')"></HeaderBlock>
  <div class="cart wrap">
    <h2>Cart</h2>
    <div class="line" v-for="item in items" :key="item">
      <p style="width: 33%;">{{ item.title }}</p>
      <p style="width: 33%;">{{ item.counter }}</p>
      <button style="width: 33%;" @click="removeItem(items.indexOf(item))">delete</button>
    </div>
  </div>
  <FooterBlock></FooterBlock>
</template>
<script>
import HeaderBlock from './HeaderBlock.vue'
import FooterBlock from './FooterBlock.vue'
export default {
  name: 'ShoppingCartPage',
  components: {
    HeaderBlock,
    FooterBlock
  },
  props: [
    'items'
  ],
  data () {
    return {
    }
  },
  mounted () {
  },
  methods: {
    removeItem (x) {
      this.$props.items.splice(x, 1)
      this.saveItems()
    },
    saveItems () {
      const parsed = JSON.stringify(this.currentItems)
      localStorage.setItem('items', parsed)
    }
  }
}
</script>
<style>
  .cart{
    display: flex;
    flex-direction: column;
  }
  .line{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    border-top: 1px solid #000;
  }
</style>
