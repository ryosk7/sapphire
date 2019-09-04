<template>
  <div>
    <div
      v-for="(user, index) in users"
      :key="index"
    >
      <ul class="list-group">
        <li class="list-group-item">
          <p>{{ user.name }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  asyncData({ $axios, params }) {
    return $axios.$get(`http://localhost:3000/users/`)
      .then((res) => {
        console.log(res)
        return { users: res }
      })
  }
}
</script>