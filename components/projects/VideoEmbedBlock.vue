<template>
  <div class="video-embed-block">
    <div
      v-if="host === 'vimeo'"
      class="video"
    >
      <iframe
        :src="'https://player.vimeo.com/video/' + videoCode"
        width="640px"
        height="360"
        frameborder="0"
        webkitallowfullscreen
        mozallowfullscreen
        allowfullscreen
      />
    </div>

    <div
      v-if="host === 'youtube'"
      class="video"
    >
      <div class="video-container">
        <iframe
          class="youtube-iframe"
          width="560"
          height="315"
          :src="'https://www.youtube.com/embed/' + videoCode"
          framborder="0"
          allowfullscreen
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
        />
      </div>
    </div>

    <div
      v-if="host === 'facebook'"
      class="video"
    >
      <iframe
        :src="url"
        width="476"
        height="476"
        style="border:none;overflow:hidden"
        scrolling="no"
        frameborder="0"
        allowTransparency="true"
        allowFullScreen="true"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoEmbedBlock',

  props: {
    host: {
      type: String,
      required: true
    },
    url: {
      type: String,
      default: ''
    },
    videoCode: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss">
@import "~@/assets/style/variables";

.video-embed-block {
  display: block;
  width: 100%;

  .video {
    text-align: center;
    iframe {
      border: none;
    }
  }
}
</style>
