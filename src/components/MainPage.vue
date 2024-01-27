<template>
  <div class="main wrap">
    <div class="mask" v-if="mask" @click="mask = false; showCardDesc = false"></div>
    <BigCardBlock :descCard="descCard" class="card-desc" v-if="showCardDesc"></BigCardBlock>
    <HeaderBlock @toGeneral="$emit('toGeneral')" @toCart="$emit('toCart')"></HeaderBlock>
    <div class="pages">
      <select class="categories" v-model="sel_cat" @change="getItems(sel_cat)">
        <option v-for="i in all_categories.length" :key="i" :value="i - 1">{{ all_categories[i - 1] }}</option>
      </select>
      <div class="page_buttons">
        <button v-for="n in btns" :key="n" v-text="n.btnText" :class="['btn', { active: currentPage === n.btnClass }]"
          v-show="len == 10" @click="swap(n.btnText, n.btnClass)"></button>
      </div>
      <PageBlock class="page" id="1" :items="all_items.slice(0, len)" v-if="page == 1" @clicked="showDesc" @count="(counted, prop) => {$emit('add', counted, prop)}">
      </PageBlock>
      <PageBlock class="page" id="2" :items="all_items.slice(len, all_items.lenght)" v-if="page == 2 && len == 10"
        @clicked="showDesc"></PageBlock>
      <div class="page_buttons">
        <button v-for="n in btns" :key="n" v-text="n.btnText" :class="['btn', { active: currentPage === n.btnClass }]"
          v-show="len == 10" @click="swap(n.btnText, n.btnClass)"></button>
      </div>
    </div>
    <FooterBlock></FooterBlock>
  </div>
</template>
<script>
import HeaderBlock from './HeaderBlock.vue'
import FooterBlock from './FooterBlock.vue'
import PageBlock from './PageBlock.vue'
import BigCardBlock from './BigCardBlock.vue'
export default {
  name: 'MainPage',
  components: {
    HeaderBlock,
    FooterBlock,
    PageBlock,
    BigCardBlock
  },
  data () {
    return {
      all_items: [],
      all_categories: [],
      page: 1,
      currentPage: 'btn1',
      len: 0,
      mask: false,
      sel_item: {},
      showCardDesc: false,
      btns: [
        {
          btnText: '1',
          btnClass: 'btn1'
        },
        {
          btnText: '2',
          btnClass: 'btn2'
        }
      ],
      descCard: {},
      sel_cat: 4
    }
  },
  methods: {
    getItems (cat) {
      this.all_items = []
      let url = new URL('https://fakestoreapi.com/products')
      if (cat !== undefined && cat !== 4) {
        url = new URL('https://fakestoreapi.com/products/category/' + this.all_categories[cat])
      }
      fetch(url)
        .then(response => response.json())
        .then(json => {
          this.all_items = json
          if (this.all_items.length < 10) {
            this.len = this.all_items.length
          } else {
            this.len = 10
          }
        })
    },
    getCategories () {
      this.all_categories = []
      const url = new URL('https://fakestoreapi.com/products/categories')
      fetch(url)
        .then(response => response.json())
        .then(json => {
          this.all_categories = json
          this.all_categories.push('none')
        })
    },
    swap (num, btn) {
      this.page = num
      window.scrollTo(0, 0)
      this.currentPage = btn
    },
    showDesc (id) {
      this.mask = true
      this.showCardDesc = true
      for (let i = 0; i < this.all_items.length; i++) {
        if (this.all_items[i].id === id) {
          this.descCard = this.all_items[i]
        }
      }
    }
    // add (a, id) {
    //   this.counter = a
    //   for (let i = 0; i < this.all_items.length; i++) {
    //     if (this.all_items[i].id === id) {
    //       this.descCard = this.all_items[i]
    //     }
    //   }
    // }
  },
  created () {
    this.getItems()
    this.getCategories()
  }
}
</script>
<style>
.wrap {}

.pages {
  padding: 2vw;
}

.mask {
  position: fixed;
  z-index: 2;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100%;
  background-color: #6666668a;
  display: flex;
  flex-direction: column;
}

.card-desc {
  position: fixed;
  z-index: 3;
  top: 10%;
  left: 25%;
  background-color: #fff;
  border: 1px solid #000;
  width: 50%;
  height: 75%;
  padding: 0;
  margin: 0;
}

.btn {
  border: 1px solid #000;
  background-color: #fff;
  width: 30px;
  height: 30px;
}

.active {
  background-color: #999999;
}

.categories {
  height: 40px;
  font-size: 20pt;
}

.page_buttons {
  margin-top: 5vw;
  margin-bottom: 5vw;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 5px;
}
</style>
