<template>
  <div class="project-card">
    <div class="project-head">
      <img :src="project.featured_media_src_url" />
    </div>
    <div class="project-body">
      <h3 class="">
        {{ project.title.rendered }}
      </h3>
      <div class="project-content" v-html="project.excerpt.rendered"></div>
    </div>
    <div class="project-footer">
      <nuxt-link
        :to="{
          name: 'projects-slug',
          params: { slug: project.slug },
        }"
        class="button"
      >
        View Project
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    project: Object,
    noText: {
      type: Boolean,
      default: false,
    },
  },
};
</script>
