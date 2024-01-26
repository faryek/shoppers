<template>
  <div class="header">
    <div class="left">
      <img src="@/assets/img/logo.jpg" alt="">
      <h1>elitno</h1>
    </div>
    <div class="right">
      <button @click="$emit('toGeneral')">General</button>
      <button @click="$emit('toCart')">Cart</button>
    </div>
  </div>
</template>
<script>
export default {

}
</script>
<style>
body{
  margin: 0;
  padding: 0;
}
.header {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  background-color: floralwhite;
  padding-left: 2vw;
  padding-right: 2vw;
}

.left{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
  gap: 5vw;
}

.right{
  display: flex;
  flex-direction: row;
  gap: 1vw;
}

.right button{
  width: 90px;
}

img {
  width: 170px;
  height: 170px;
}

h1 {
  font-size: 35pt;
}
</style>
