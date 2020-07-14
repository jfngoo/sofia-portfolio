<template>
  <div class="about">
    <img
      class="photo"
      src="../assets/img/contact/photo.jpg"
      alt="Sofia Boggio"
    >
    <div class="text-wrapper">
      <div class="text">
        <div class="title">
          {{ $t('title') }}
        </div>
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
  name: 'About',

  mounted () {
    console.log(this.$t('about'))
  }
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

  & > .photo {
    flex: 0 0 435px;
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
