<template>
  <div class="about">
    <div class="photo" />
    <div class="text-wrapper">
      <div class="text">
        <h1 class="title">
          {{ $t('title') }}
        </h1>
        <div class="subtitle">
          <p v-html="$t('subtitle')" />
          <br>
          <p v-html="$t('about')" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'About'
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/variables";

.about {
  display: flex;
  background: $main_color;
  color: $font_color;
  margin-left: 115px;

  flex-wrap: wrap;

  @media screen and (max-width: $breakpoint-sm) {
    display: block;
    margin-left: 0;
  }

  & > .photo {
    min-height: 556px;
    flex: 0 0 435px;
    background: url('../assets/img/contact/photo.jpg') no-repeat center center;
    background-size: cover;
  }

  & > .text-wrapper {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 50px;

    & > .text {
      display: inline-block;
      max-width: 550px;

      & > .title {
        font-family: $zilla_slab;
        font-size: $f64;
        line-height: $f60;
        margin-bottom: 36px;
      }

      & > .subtitle {
        font-size: $f24;
        line-height: $f41;
      }
    }
  }
}
</style>
