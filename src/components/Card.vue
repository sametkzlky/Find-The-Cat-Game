<template>
    <div class="card">
        <img :src="card.image" alt="" />
      </div>
</template>
<script>
export default{
    props :["card"],
}
</script>
<style scoped>
.card {
  width: 200px;
  height: 230px;
  border-radius: 5px;
  border: 1px solid #666;
  cursor: pointer;
}
.card:hover {
  box-shadow: 0px 5px 48px #666;
  transition: box-shadow 0.5s;
}
.card img {
  width: 100%;
  height: 100%;
}
</style>
</style>