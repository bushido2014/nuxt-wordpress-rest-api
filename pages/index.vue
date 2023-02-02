<template>
  <div>
    <Hero />
    <section class="skills" id="skills">
      <div class="section_title">
        <h1>SKILLS</h1>
      </div>
      <div class="container">
        <Skills />
      </div>
    </section>
    <section class="home-projects">
      <div class="section_title">
        <h1>Projects</h1>
      </div>
      <div class="container">
        <div class="project-list grid">
          <nuxt-link
            v-for="(project, i) in projects"
            :key="i"
            :to="`/projects/${project.slug}/`"
            class="project-list__card"
          >
            <ProjectList :project="project" :no-text="true" />
          </nuxt-link>
        </div>
        <div class="project-list-link">
          <nuxt-link to="/projects" class="button"
            >View All Projects
          </nuxt-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Hero from '~/components/Hero';
import Skills from '~/components/Skills';
import ProjectList from '~/components/ProjectList';
export default {
  components: { Hero, Skills, ProjectList },
  async asyncData() {
    const response = await fetch(
      `${process.env.baseURL}/wp-json/wp/v2/projects?per_page=3`
    );
    const projects = await response.json();
    return { projects };
  },
};
</script>
