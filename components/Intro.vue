<template>
  <div class="intro">
    <h1>
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

  h1 {
    font-family: $zilla_slab;
    font-size: $f76;
    line-height: $f80;
    margin-bottom: 16px;
  }

  .subtitle {
    font-size: $f32;
    line-height: $f48;
  }
}
</style>
