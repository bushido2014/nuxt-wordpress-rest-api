<template>
  <article class="post">
    <nuxt-link
      :to="{ name: 'blog-slug', params: { slug: post.slug } }"
      class="entry-title"
    >
      <div class="post-header">
        <img
          v-if="post.image"
          class="post-image"
          :src="post.image"
          :alt="post.title.rendered"
        />
      </div>
      <div class="post-title">
        <h1>
          {{ post.title.rendered }}
        </h1>
      </div>
    </nuxt-link>
    <div class="entry-content" v-html="post.excerpt.rendered"></div>
    <div class="continue-reading">
      <nuxt-link
        :to="{ name: 'blog-slug', params: { slug: post.slug } }"
        class="button"
        >Read more
      </nuxt-link>
    </div>
  </article>
</template>
<script>
export default {
  props: ['post'],
};
</script>
