<template>
  <div class="card">
    <div class="upper">
      <img class="img" :src="img" alt="404">
      <p>{{name}}</p>
      <p>{{price}}$</p>
    </div>
    <div style="display: flex; flex-direction: column; gap: 0;">
      <div class="add">
        <button @click="counter--">-</button>
        <p>{{counter}}</p>
        <button @click="counter++">+</button>
      </div>
      <button class="adder" @click="$emit('add', counter)">add to cart</button>
    </div>
    <div class="lower">
      <p style="text-align: left;">{{category}}</p>
      <button @click="$emit('clicker')">more</button>
      <p style="text-align: right;">{{rate}}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ['img', 'name', 'price', 'category', 'rate'],
  data () {
    return {
      counter: 0
    }
  },
  methods: {
  }
}
</script>
<style>
.img{
  width: 10vw;
  height: 10vw;
}
.card {
  border: 1px solid #000;
  width: 25%;
  min-height: 520px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding-top: 3vw;
}

.upper{
  text-align: center;
}

.upper p{
  font-size: 18pt;
}

.add{
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 0;
}

.adder{
  width: 134px;
  font-size: 16pt;
  height: 40px;
  margin: 0;
  padding: 0;
}

.add p{
  display: flex;
  border-top: 1px solid #000;
  border-bottom: 1px solid #000;
  padding-left: 2px;
  padding-right: 2px;
  width: 50px;
  height: 60px;
  align-items: center;
  justify-content: center;
  font-size: 16pt;
  margin: 0;
}

.add button{
  height: 62px;
  width: 40px;
  font-size: 16pt;
}

.lower {
  background-color: floralwhite;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 90%;
  padding-left: 5%;
  padding-right: 5%;
}

.lower p{
  width: 33%;
}

.lower button{
  width: 33%;
  font-size: 16pt;
}
</style>
