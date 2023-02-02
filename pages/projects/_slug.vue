<template>
  <div class="container">
    <article
      v-for="project in projects"
      :key="project.id"
      class="single-project"
    >
      <div class="project-single__link">
        <nuxt-link to="/projects" class="button"
          >Back to All Projects
        </nuxt-link>
      </div>
      <div class="single-project__title">
        <h1>
          {{ project.title.rendered }}
        </h1>
      </div>
      <div class="single-project__img">
        <img :src="project.featured_media_src_url" />
      </div>

      <div class="single-project__content">
        <div
          v-if="project.content"
          class="mt-5 content"
          v-html="project.content.rendered"
        ></div>
      </div>
    </article>
  </div>
</template>

<script>
export default {
  async asyncData({ params, error }) {
    const response = await fetch(
      `${process.env.baseURL}/wp-json/wp/v2/projects/?slug=${params.slug}&_embed=1`
    );
    const projects = await response.json();

    if (projects.length <= 0) {
      return error({ statusCode: 404, message: 'Page not found' });
    }

    console.log(projects[0]);
    return { projects };
  },
  head() {
    return {
      title: this.projects[0].title.rendered,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.projects[0].excerpt.rendered,
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: this.projects[0].title.rendered,
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.projects[0].excerpt.rendered,
        },
        {
          hid: 'og:type',
          property: 'og:type',
          content: 'projects',
        },
      ],
    };
  },
};
</script>
