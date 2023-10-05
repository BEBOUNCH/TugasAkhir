<template>
  <div class="container mb-2">
    <form id="tambah-artikel" @submit.prevent="onFormSubmit">
      <div class="form-group mb-4">
        <label for="file" class="text-white my-2">Upload Image:</label>
        <br>
        <input id="file" ref="fileInput" type="file">
      </div>
      <button class="btn btn-primary" type="submit">Add Image</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return{
    }
  },
  methods: {
    async onFormSubmit () {
      const fileInput = this.$refs.fileInput;
      const dataForm = {
        image: fileInput.files[0].name
        // image: document.getElementById("image").value,
      }
      console.log(dataForm)
      const response = await fetch(process.env.supabaseApi + '/storage/v1/object/public/photoCard/', {
        method: 'POST',
        headers: {
          apikey: process.env.supabaseKey,
        },
        body: FormData(dataForm)
      })
      const data = await response?.json()
      // this.$router.push(`/${fileInput.files[0].name}`)
      this.$router.push(`/${data[0]?.id}`)
    }
  }
}
</script>