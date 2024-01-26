<template>
  <div class="card">
    <div class="card-top">
      <h2>{{ descCard.title }}</h2>
      <p>{{ descCard.category }}</p>
    </div>
    <div class="card-mid">
      <img :src="descCard.image" alt="">
      <p>{{ descCard.description }}</p>
    </div>
    <div class="card-bot">
      <p>{{ descCard.price }}$</p>
      <div class="card-rate">
        <p class="rate">{{ descCard.rating.rate }}/</p>
        <p class="count">{{ descCard.rating.count }} votes</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ['descCard']
}
</script>
<style>
h2{
  padding: 0;
  margin: 0;
  font-size: 20pt;
}

.card{
}

.card-top{
  padding-top: 1vw;
  padding-left: 10%;
  padding-right: 10%;
  display: flex;
  flex-direction: column;
  width: 80%;
}

.card-top p{
  font-size: 18pt;
}

.card-mid{
  padding-left: 10%;
  padding-right: 10%;
  display: flex;
  flex-direction: row;
  width: 80%;
  gap: 1vw;
}

.card-mid p{
  font-size: 12pt;
  width: 70%;
}

.card-bot{
  padding-left: 10%;
  padding-right: 10%;
  display: flex;
  flex-direction: row;
  width: 80%;
  justify-content: space-between;
}

.card-rate{
  display: flex;
  flex-direction: row;
}

.rate{
  font-weight: bold;
}
</style>
