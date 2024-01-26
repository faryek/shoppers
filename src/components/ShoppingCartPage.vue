<template>
  <HeaderBlock @toGeneral="$emit('toGeneral')" @toCart="$emit('toCart')"></HeaderBlock>
  <div class="cart wrap">
    <h2>Cart</h2>
  </div>
  <FooterBlock></FooterBlock>
</template>
<script>
import HeaderBlock from './HeaderBlock.vue'
import FooterBlock from './FooterBlock.vue'
// import PageBlock from './PageBlock.vue'
export default {
  name: 'ShoppingCartPage',
  components: {
    HeaderBlock,
    FooterBlock
    // PageBlock
  },
  data () {
    return {
    }
  }
}
</script>
<style></style>
