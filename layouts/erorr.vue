<template>
  <div>
    <!-- 404 -->
    <h1 v-if="error.statusCode === 404">404: ページが見つかりません</h1>
    <!-- other -->
    <h1 v-else>500: エラーが生じました。</h1>
    <!-- button -->
    <nuxt-link to="/" class="btn">home</nuxt-link>
  </div>
</template>

<script>
export default {
  props: ['error'],
  layout: 'error',
}
</script>

<style>
.btn {
  @apply bg-green-600 hover:bg-green-900 text-white rounded px-4 py-2;
}
</style>