<template>
  <div class="project">
    <Topbar />
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

      <InfoBar
        :title="project.title"
        :date="project.date"
        :type="project.type"
        :skills="project.skills"
        :team="project.team"
      />
      <div class="container">
        <div
          v-for="(row, i) in project.rows"
          :key="`row-${i}`"
          :class="{ fullsize: row.rowType === 'fullsize' }"
          class="row"
        >
          <div
            v-for="(block, j) in row.blocks"
            :key="`row-${i}-block-${j}`"
            :class="{ full: block.type === '2col' || block.block === 'video-embed' }"
            class="block"
          >
            <TextBlock
              v-if="block.block === 'text'"
              :subtitle="block.subtitle"
              :title="block.title"
              :text="block.text"
            />
            <ImageBlock
              v-if="block.block === 'image'"
              :id-project="project.id"
              :type="block.type"
              :image="block.image"
            />
            <ImageRow
              v-if="block.block === 'image-row'"
              :id-project="project.id"
              :image="block.image"
            />
            <VideoEmbedBlock
              v-if="block.block === 'video-embed'"
              :host="block.host"
              :url="block.url"
              :video-code="block.videoCode"
              :video-width-height-ratio="parseFloat(block.videoWidthHeightRatio) || 1.77"
              :video-total-width-ratio="parseFloat(block.videoTotalWidthRatio) || 1.4"
            />
          </div>
        </div>
      </div>
      <NextBar
        :previous="previousProject"
        :next="nextProject"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Project',

  computed: {
    projects () {
      return this.$i18n.messages[this.$i18n.locale].projects
    },

    project () {
      return this.projects.find(x => x.id === this.$route.params.id)
    },

    projectIndex () {
      return this.projects.findIndex(x => x.id === this.$route.params.id)
    },

    previousProject () {
      return this.projectIndex > 0 ? this.projects[this.projectIndex - 1] : this.projects[this.projects.length - 1]
    },

    nextProject () {
      return this.projectIndex < this.projects.length - 1 ? this.projects[this.projectIndex + 1] : this.projects[0]
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

  & > .project-container {
    & > .container {
      padding: 0;

      .row {
        display: flex;
        padding: 0 115px;
        margin: 104px 0;

        @media screen and (max-width: $breakpoint-md) {
          padding: 0 $medium-padding;
        }

        @media screen and (max-width: $breakpoint-sm) {
          padding: 0 24px;
          flex-wrap: wrap;
        }

        & > .block {
          flex: 0.5;

          @media screen and (max-width: $breakpoint-sm) {
            flex: 0 0 100%;
          }

          &.full {
            flex: 1;
          }
        }

        &.fullsize {
          padding: 0;

          & > .block {
            flex: 1;
          }
        }

        & > .block + .block {
          margin-left: 25px;

          @media screen and (max-width: $breakpoint-sm) {
            margin-left: 0;
          }
        }
      }
    }
  }
}
</style>
