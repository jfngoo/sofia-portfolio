<template>
  <div class="intro">
    <h1 class="title">
      {{ $t('title') }}
    </h1>

    <p class="subtitle" v-html="$t('subtitle')" />
  </div>
</template>

<script>
export default {
  name: 'Intro'
}
</script>

<style lang="scss">

@import '../assets/style/variables';

.intro {
  color: $font_color;
  max-width: 834px;

  & > h1.title {
    margin-bottom: 16px;
    font-family: $zilla_slab;
    font-size: $f76;
    line-height: $f80;

    @media all and (max-width: $breakpoint-sm) {
      font-size: $f48;
      line-height: $f50;
    }
  }

  & > p.subtitle {
    font-size: $f32;
    line-height: $f48;

    @media all and (max-width: $breakpoint-sm) {
      font-size: $f22;
      line-height: $f33;
    }
  }
}
</style>
