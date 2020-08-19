<template>
  <div class="about">
    <div class="photo" />
    <div class="text-wrapper">
      <div class="wrapper">
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
      <Contact />
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
  color: $font_color;
  flex-wrap: wrap;

  @media screen and (max-width: $breakpoint-md) {
    padding: 0 64px;
    display: block;
  }

  @media screen and (max-width: $breakpoint-sm) {
    display: block;
    margin-left: 0;
    padding: 0;
  }

  & > .photo {
    height: 488px;
    width: 435px;
    top: 146px;
    left: calc(#{$menu_width} + 90px);
    position: fixed;
    background: url('../assets/img/contact/photo.jpg') no-repeat 10% center;
    background-size: cover;

    @media screen and (max-width: $breakpoint-md) {
      position: inherit;
      width: 100%;
    }

    @media screen and (max-width: $breakpoint-sm) {
      position: inherit;
      width: 100%;
    }
  }

  & > .contact {
    margin-left: calc(435px + 90px);
    padding-left: 50px;
  }

  & > .text-wrapper {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    margin-left: calc(435px + 90px);

    @media screen and (max-width: $breakpoint-md) {
      align-items: flex-start;
      margin-left: 0;
    }

    @media screen and (max-width: $breakpoint-sm) {
      align-items: center;
      margin-left: 0;
    }

    & > .wrapper {
      background: $main_color;
      padding: 60px;
      width: 100%;

      @media screen and (max-width: $breakpoint-md) {
        padding: 100px;
      }

      @media screen and (max-width: $breakpoint-sm) {
        padding: 50px;
      }

      & > .text {
        display: inline-block;
        width: 550px;

        @media screen and (max-width: $breakpoint-md) {
          width: 100%;
        }

        & > .title {
          font-family: $zilla_slab;
          font-size: $f64;
          line-height: $f60;
          margin-bottom: 36px;
        }

        & > .subtitle {
          font-size: $f20;
          line-height: $f28;
        }
      }
    }
  }
}
</style>
