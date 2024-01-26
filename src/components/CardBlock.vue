<template>
  <div class="card">
    <div class="upper">
      <img class="img" :src="img" alt="404">
      <p>{{name}}</p>
      <p>{{price}}$</p>
    </div>
    <div class="lower">
      <p>{{category}}</p>
      <p>{{rate}}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ['img', 'name', 'price', 'category', 'rate']
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
  min-height: 350px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding-top: 3vw;
}

.upper{
  text-align: center;
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
</style>
