<template>
  <div class="container my-2">
    <h3 class="text-white my-4">Administrator Cards</h3>
    <nuxt-link to="/adminPage/form/TambahImage" class="btn btn-primary mt-2">Add Image</nuxt-link>
    <div class="row justify-content-between">
      <CardItemAdmin
          v-for="(card, i) in cards"
          :key="i"
          :card="card"
          class="col-md-4"
        />
    </div>
    <nuxt-link to="/adminPage/form/TambahCard" class="btn btn-primary mt-2">Add Cart</nuxt-link>
  </div>
</template>
<script>
import CardItemAdmin from "@/components/adminPage/CardAdmin/CardItemAdmin.vue"
export default {
  components: {
    CardItemAdmin
  },
  layout: 'admin',
  data() {
    return {
      // Daftar task
      cards: []
    }
  },
  mounted() {
      this.getCards();
    },
    methods: {
      async getCards() {
        const response = await this.$axios.get("/rest/v1/cards", {
          headers: {
            apikey: process.env.supabaseKey
          }
        })
        this.cards = response?.data
      },
    }
  }
</script>
<style scoped>
  /* img{
    display: block;
  } */
</style>