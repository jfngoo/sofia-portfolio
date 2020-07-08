<template>
  <div class="home">
    <Sidebar />
    <div class="intro-container">
      <Intro />
    </div>
    <div class="projects-container">
      <nuxt-link
        v-for="project in projects"
        :key="project.title"
        :to="`/${project.id}`"
      >
        <ProjectThumbnail
          :id="project.id"
          :title="project.title"
          :subtitle="project.subtitle"
        />
      </nuxt-link>
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
  },

  head () {
    return {
      title: 'Sofia Boggio - Freelance interactive designer',
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: 'Sofia Boggio\'s portfolio' }
      ]
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

  @media all and (max-width: $breakpoint-sm) {
    padding: 0 24px 30px;
  }
}

.intro-container {
  min-height: 100vh;
  display: flex;
  align-items: flex-end;
  padding: 0 90px 115px;

  @media all and (max-width: $breakpoint-sm) {
    min-height: auto;
    padding: 200px 24px 60px;
  }
}

.project-thumbnail {
  margin: 40px 90px;

  @media screen and (max-width: $breakpoint-sm) {
    margin: 24px 0;
  }
}
</style>
