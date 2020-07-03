<template>
  <div class="project-thumbnail">
    <div class="thumbnail">
      <div class="text">
        <h2 class="project-thumbnail-title">
          {{ title }}
        </h2>
        <h3 class="project-thumbnail-subtitle">
          {{ subtitle }}
        </h3>
      </div>
      <div class="start-button">
        {{ $t('view-project') }}
      </div>
    </div>
    <div class="thumbnail-bg" />
  </div>
</template>

<script>
export default {
  name: 'ProjectThumbnail',

  props: {
    title: {
      type: String,
      default: ''
    },
    subtitle: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss">
@import '../assets/style/variables';

.project-thumbnail {
  height: 460px;
  background: red;
  position: relative;
  color: white;

  @media screen and (max-width: $breakpoint-sm) {
    height: 345px;
  }

  & > .thumbnail, & > .thumbnail-bg {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
  }

  & > .thumbnail {
    background: red;
    z-index: 2;
    transition: top 0.3s cubic-bezier(0.16, 1, 0.3, 1), left 0.3s cubic-bezier(0.16, 1, 0.3, 1);

    display: flex;
    justify-content: flex-start;
    align-items: center;

    &:hover {
      cursor: pointer;
    }

    @media all and (min-width: $breakpoint-sm) {
      &:hover {
        top: -10px;
        left: -10px;
      }
    }

    & > .text {
      margin-left: 115px;
      margin-right: 50px;

      @media all and (max-width: $breakpoint-sm) {
        margin-left: 24px;
      }

      & > h2.project-thumbnail-title {
        font-family: $zilla_slab;
        font-size: $f76;
        line-height: $f80;

        @media all and (max-width: $breakpoint-sm) {
          font-size: $f40;
          line-height: $f32;
        }
      }

      & > h3.project-thumbnail-subtitle {
        margin-top: 12px;
        font-size: $f20;
        line-height: $f26;

        @media screen and (max-width: $breakpoint-sm) {
          font-size: $f14;
          line-height: $f20;
        }
      }
    }

    & > .start-button {
      background: white;
      font-style: normal;
      font-weight: normal;
      font-size: $f16;
      line-height: $f28;

      display: inline-flex;
      align-items: center;
      text-align: center;
      padding: 12px;
      color: $main_color;
      position: absolute;
      bottom: 30px;
      right: 30px;

      @media all and (min-width: $breakpoint-sm) {
        display: none;
      }
    }
  }

  & > .thumbnail-bg {
    z-index: 1;
    background: $main_color;
  }
}
</style>
