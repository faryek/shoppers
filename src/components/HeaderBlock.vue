<template>
  <div class="header">
    <img src="@/assets/img/logo.jpg" alt="">
    <h1>резня</h1>
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
  justify-content: flex-start;
  gap: 5vw;
  background-color: floralwhite;
  padding-left: 2vw;
}

img {
  width: 170px;
  height: 170px;
}

h1 {
  font-size: 35pt;
}
</style>
