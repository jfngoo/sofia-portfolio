<template>
  <div class="project">
    <Sidebar />
    <div class="project-container">
      <div
        class="banner project-banner"
        :style="{ backgroundImage: `url('${require(`../assets/img/posters/${project.id}.jpg`)}')` }"
      >
        <div class="text">
          <h1 class="title">
            {{ project.title }}
          </h1>
          <h2 class="subtitle">
            {{ project.subtitle }}
          </h2>
        </div>
      </div>
    </div>
    <InfoBar
      :title="project.title"
      :date="project.date"
      :type="project.type"
      :skills="project.skills"
      :team="project.team"
    />
    <div class="container">
      <div class="row">
        <TextBlock />
        <TextBlock />
      </div>
      <div class="row">
        <VideoEmbedBlock
          host="facebook"
          url="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2FOrange.France%2Fvideos%2F795742717528294%2F&show_text=0&width=476"
        />
      </div>
      <div class="row">
        <TextBlock />
        <ImageBlock
          :id-project="project.id"
          image="image-1.png"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Project',

  computed: {
    project () {
      return this.$i18n.messages[this.$i18n.locale].projects.find(x => x.id === this.$route.params.id)
    }
  },

  head () {
    return {
      title: `Sofia Boggio - ${this.project.title}`,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: this.project.subtitle }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/fonts';
@import '../assets/style/variables';
@import '../assets/style/typo';

.project {
  background: $grey4;
  font-family: $barlow;
  padding-left: $menu_width;
  padding-bottom: 60px;
  color: $font_color;

  @media all and (max-width: $breakpoint-sm) {
    padding: 0;
  }

  .banner {
    width: 100%;
    height: 530px;
    background: center center no-repeat;
    background-size: cover;
    display: flex;
    align-items: center;
  }

  & > .container {
    padding: 80px 115px;

    .row {
      display: flex;

      .block {
        flex: 0.5;
      }

      & > .block + .block {
        margin-left: 25px;
      }

      & + .row {
        margin-top: 104px;
      }
    }
  }
}
</style>
