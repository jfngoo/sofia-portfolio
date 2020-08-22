<template>
  <div class="video-embed-block">
    <div
      v-if="host === 'vimeo'"
      class="video"
    >
      <iframe
        :src="'https://player.vimeo.com/video/' + videoCode"
        :width="ratioWidth"
        :height="ratioHeight"
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
        width="300"
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
import debounce from 'lodash.debounce'

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
    },
    videoWidthHeightRatio: {
      type: Number,
      default: 1.777 // 16/9
    },
    videoTotalWidthRatio: {
      type: Number,
      default: 1.4
    }
  },

  data () {
    return {
      width: 300,
      height: 300
    }
  },

  computed: {
    debouncedHandleResize () {
      return debounce(this.handleResize, 100)
    },

    ratioWidth () {
      return this.width / this.videoTotalWidthRatio
    },

    ratioHeight () {
      const ratioHeight = this.ratioWidth / this.videoWidthHeightRatio
      return ratioHeight > this.height / 1.2 ? this.height / 1.2 : ratioHeight
    }
  },

  mounted () {
    window.addEventListener('resize', this.debouncedHandleResize)
    this.handleResize()
  },

  methods: {
    handleResize () {
      this.width = window.innerWidth
      this.height = window.innerHeight
    }
  }
}
</script>

<style lang="scss">
@import "~@/assets/style/variables";

.video-embed-block {
  display: block;
  width: 100%;
  overflow: hidden;

  .video {
    text-align: center;
    iframe {
      border: none;
    }
  }
}
</style>
