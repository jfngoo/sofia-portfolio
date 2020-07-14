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
        :to="localePath(`/${project.id}`)"
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

export default Vue.extend({
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
  color: $font_color;

  @media all and (max-width: $breakpoint-md) {
    padding: 0 0 10px $menu_width;
  }

  @media all and (max-width: $breakpoint-sm) {
    padding: 0 24px 30px;
  }
}

.intro-container {
  min-height: 100vh;
  display: flex;
  align-items: flex-end;
  padding: 0 $large-padding 115px;

  @media screen and (max-width: $breakpoint-md) {
    padding: 0 $medium-padding 60px;
  }

  @media all and (max-width: $breakpoint-sm) {
    min-height: auto;
    padding: 200px 24px 60px;
  }
}

.project-thumbnail {
  margin: 40px $large-padding;

  @media screen and (max-width: $breakpoint-md) {
    margin: $medium-padding;
  }

  @media screen and (max-width: $breakpoint-sm) {
    margin: 24px 0;
  }
}
</style>
