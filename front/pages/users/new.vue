<template>
  <section>
    <div>
      <h1>New user</h1>
      <form id='app' @submit='onSubmit' action='' method='post'>
        <label for="name">Name: </label>
        <input type='text' name='user[name]' id='name' v-model='name'>
        <input
          type='file'
          @change='selectedFile'
          name='user[picture]'
          accept='image/*'
          placeholder='Upload file...'
        />
        <button type="submit">submit</button>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      picture: null,
      uploadFile: null
    }
  },
  methods: {
    post() {
      this.$axios.post(
        'http://localhost:3000/users',
        {
          name: this.name,
          file: this.file
        }
      ).then((res) => {
        this.$router.push(`${res.data.id}`)
      })
    },
    selectedFile: function (e) {
      e.preventDefault()
      const files = e.target.files
      this.uploadFile = files[0]
    },
    onSubmit: function (e) {
      e.preventDefault()
      const formData = new FormData()
      formData.append('user[name]', this.name)
      formData.append('user[picture]', this.uploadFile)
      this.$axios.post('http://localhost:3000/users', formData)
        .then(res => {
          this.$router.push(`${res.data.id}`)
        })
    }
  }
}
</script>