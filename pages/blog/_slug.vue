<template>
  <div class="container">
    <article v-for="post in posts" :key="post.id" class="single-post">
      <div class="single-post-title">
        <h1 class="title">
          {{ post.title.rendered }}
        </h1>
      </div>
      <div class="single-post-content">
        <div
          v-if="post.content"
          class="mt-5 content"
          v-html="post.content.rendered"
        ></div>
      </div>
    </article>
  </div>
</template>

<script>
export default {
  async asyncData({ params, error }) {
    const response = await fetch(
      `${process.env.baseURL}/wp-json/wp/v2/posts/?slug=${params.slug}&_embed=1`
    );
    const posts = await response.json();

    if (posts.length <= 0) {
      return error({ statusCode: 404, message: 'Page not found' });
    }

    console.log(posts[0]);
    return { posts };
  },
  head() {
    return {
      title: this.posts[0].title.rendered,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.posts[0].excerpt.rendered,
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: this.posts[0].title.rendered,
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.posts[0].excerpt.rendered,
        },
        {
          hid: 'og:type',
          property: 'og:type',
          content: 'blog',
        },
      ],
    };
  },
};
</script>
