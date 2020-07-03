<template>
  <div class="project-thumbnail">
    <div class="thumbnail">
      <div class="text">
        <h2 class="title">
          {{ title }}
        </h2>
        <h3 class="project-subtitle">
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
      top: -10px;
      left: -10px;
      cursor: pointer;
    }

    & > .text {
      margin-left: 115px;

      & > h2.title {
        color: white;
      }

      & > h3.project-subtitle {
        margin-top: 12px;
        font-size: $f20;
        line-height: $f26;
      }
    }

    & > .start-button {
      background: white;
      font-style: normal;
      font-weight: normal;
      font-size: 16px;
      line-height: 28px;

      display: inline-flex;
      align-items: center;
      text-align: center;
      padding: 12px;
      color: $main_color;
      position: absolute;
      bottom: 30px;
      right: 30px;
    }
  }

  & > .thumbnail-bg {
    z-index: 1;
    background: $main_color;
  }
}
</style>
