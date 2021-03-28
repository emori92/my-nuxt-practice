<template>
  <div>
    <!-- link -->
    <nuxt-link to="/" class="btn">Home</nuxt-link>
    <nuxt-link to="/fun/" class="btn">fun</nuxt-link>
  </div>
</template>


<style>
.btn {
  @apply bg-green-600 hover:bg-green-900 text-white rounded px-4 py-2;
}
</style>