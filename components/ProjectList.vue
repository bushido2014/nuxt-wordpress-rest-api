<template>
  <div
    class="project-list__img"
    v-bind:style="{
      'background-image': 'url(' + project.featured_media_src_url + ')',
    }"
  ></div>
</template>
<script>
export default {
  props: ['project'],
};
</script>
