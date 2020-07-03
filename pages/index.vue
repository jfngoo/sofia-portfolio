<template>
  <div class="home">
    <Sidebar />
    <div class="intro-container">
      <Intro />
    </div>
    <div class="projects-container">
      <ProjectThumbnail
        v-for="project in projects"
        :key="project.title"
        :title="project.title"
        :subtitle="project.subtitle"
      />
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import ProjectThumbnail from '../components/ProjectThumbnail'

export default Vue.extend({
  components: { ProjectThumbnail },

  computed: {
    projects () {
      return this.$i18n.messages[this.$i18n.locale].projects
    }
  }
})
</script>

<style lang="scss">

@import '../assets/style/fonts';
@import '../assets/style/variables';
@import '../assets/style/typo';

.home {
  background: $grey4;
  font-family: $barlow;
  padding-left: $menu_width;
  padding-bottom: 60px;
}

.intro-container {
  min-height: 100vh;
  display: flex;
  align-items: flex-end;
  padding: 0 90px 115px;
}

.project-thumbnail {
  margin: 40px 90px;
}
</style>
