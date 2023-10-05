<template>
  <div class="p-3">
    <div class="card">
      <img :src="card.img" class="card-img-top image" alt="err">
      <div class="card-body">
        <h5 class="card-title text-white">{{card.title}}</h5>
        <p class="card-text text-truncate text-white">{{card.description}}</p>
        <a href="#" class="text-warning" target="_blank">Continue Learning</a>
        <br>
        <nuxt-link :to="`/detail/${articleId}`" class="btn btn-primary mt-2">Edit This</nuxt-link>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    card: {
      type: Object,
      default: () => {}
    }
  }
}
</script>
<style scoped>
  .card-body{
    background-color:rgb(50, 50, 50);
  }
</style>