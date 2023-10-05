<template>
  <div class="container my-2">
    <form id="tambah-artikel" @submit.prevent="onFormSubmit">
      <div class="form-group my-2">
        <label for="title" class="text-white">Judul Artikel</label>
        <input id="title" type="text" class="form-control" name="title">
      </div>
      <div class="form-group my-2">
        <label for="description" class="text-white">Example textarea</label>
        <textarea id="description" class="form-control" name="description" rows="3"></textarea>
      </div>
      <div class="form-group my-2">
        <label for="img" class="text-white">Link Image</label>
        <input id="img" type="text" class="form-control" name="img">
      </div>
      <div class="form-group my-2">
        <label for="link" class="text-white">Link Web</label>
        <input id="link" type="text" class="form-control" name="link">
      </div>
      <button class="btn btn-primary" type="submit">Tambah Article</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return{}
  },
  methods: {
    async onFormSubmit () {
      // const formTambah = document.getElementById('tambah-artikel')
      // const formData = new formTambah(formTambah)
      const dataForm = {
        title: document.getElementById("title").value,
        description: document.getElementById("description").value,
        img: document.getElementById("img").value,
        link: document.getElementById("link").value,
      }
      const response = await fetch(process.env.supabaseApi + '/rest/v1/Article', {
        method: 'POST',
        headers: {
          apikey: process.env.supabaseKey,
          "Content-Type": "application/json",
          Prefer: "return=representation"
        },
        body: JSON.stringify(dataForm)
      })
      const data = await response?.json()
      this.$router.push(`/detail/${data[0]?.id}`)
      console.log(data)
    }
  }
}
</script>