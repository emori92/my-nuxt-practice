<template>
  <div class="container flex flex-col">
    <h1>Django REST APIのテスト</h1>
    <!-- form -->
    <div class="flex flex-col my-5">
      <label for="username">username
        <input type="text" v-model="username" class="border" />
      </label>
      <label for="password">password
        <input type="password" v-model="password" class="border" />
      </label>
      <button class="btn mt-5">Login!</button>
    </div>
    <!-- json -->
    <ul>
      <li v-for="user of response" :key="user.id" class="mt-5 p-5 rounded-lg text-left bg-green-50">
        <p>id: {{ user.id }}</p>
        <p>user name: {{ user.username }}</p>
        <p>date join: {{ user.date_joined }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
export default {
  // auth
  data() {
    return {
      username: '',
      password: '',
    }
  },
  // get users
  async asyncData({ app, error }) {
    // urls
    const url = 'http://localhost:8000'
    const jwtUrl = url + '/auth/jwt/create'
    const usersUrl = url + '/apiv1/users'
    // token
    const user = { username: 'djoser', password: 'alpine12'}
    const jwt = await app.$axios.$post(jwtUrl, user)
    const token = jwt.access
    app.$axios.setToken(token, 'JWT')
    try {
      // request
      const response = await app.$axios.$get(usersUrl)
      return { response }
      // error
    } catch (e) {
      error(e) // スローしたエラーと一緒に nuxt エラーページを表示します
    }
  },
}
</script>