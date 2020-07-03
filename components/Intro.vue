<template>
  <div class="intro">
    <h1 class="title">
      {{ $t('title') }}
    </h1>

    <p class="subtitle" v-html="subtitle" />
  </div>
</template>

<script>
import DOMPurify from 'dompurify'

export default {
  computed: {
    subtitle () {
      return DOMPurify.sanitize(this.$t('subtitle'))
    }
  }
}
</script>

<style lang="scss">

@import '../assets/style/variables';

.intro {
  color: $font_color;
  max-width: 834px;

  & > h1.title {
    margin-bottom: 16px;
  }

  & > p.subtitle {
    font-size: $f32;
    line-height: $f48;
  }
}
</style>
