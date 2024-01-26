<template>
  <div class="page">
    <div class="row" v-for="i in 3" :key="i">
      <CardBlock v-for="prop in items.slice((i - 1) * 4, (i - 1) * 4 + 4)" :key="prop" :name="prop.title"
        :img="prop.image" :price="prop.price" :category="prop.category" :rate="prop.rating.rate"
        @click="$emit('clicked', prop.id)"></CardBlock>
    </div>
  </div>
</template>
<script>
import CardBlock from './CardBlock.vue'
export default {
  name: 'PageBlock',
  components: {
    CardBlock
  },
  props: ['items'],
  data () {
    return {
    }
  }
}
</script>
<style>
.page {
  display: flex;
  flex-direction: column;
  gap: 5vw;
}

.row {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-evenly;
  gap: 1vw;
}
</style>
