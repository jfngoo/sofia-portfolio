<template>
  <div class="intro">
    <h1>
      {{ $t('title') }}
    </h1>

    <h2>
      {{ $t('subtitle') }}
    </h2>
  </div>
</template>

<script>
export default {
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

  h2 {
    font-size: $f32;
    line-height: $f48;
  }
}
</style>
