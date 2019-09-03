<template>
  <div>
    <h1>{{ data }}</h1>
  </div>
</template>

<script>
export default {
  asyncData({ $axios, params }) {
    return $axios.$get(`http://localhost:3000/users/`)
      .then((res) => {
        console.log(res)
        return { data: res }
      })
  }
}
</script>