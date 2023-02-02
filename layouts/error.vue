<template>
  <div class="container">
    <section class="error">
      <h1 v-if="error.statusCode === 404">Page not found</h1>
      <h1 v-else>An error occurred</h1>
      <NuxtLink to="/" class="error-button">Go to Home page</NuxtLink>
    </section>
  </div>
</template>

<script>
export default {
  props: ['error'],
};
</script>
