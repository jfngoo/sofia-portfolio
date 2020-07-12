<template>
  <div class="sidebar">
    <nuxt-link
      :to="localePath('/')"
      class="logo"
    >
      <img
        src="../assets/img/logo.svg"
        alt="Logo"
      >
    </nuxt-link>
    <div class="locale-selector">
      <nuxt-link
        v-for="locale in availableLocales"
        :key="locale"
        :to="switchLocalePath(locale)"
        :class="{ active: locale === $i18n.locale }"
      >
        {{ locale }}
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Sidebar',

  computed: {
    availableLocales () {
      return this.$i18n.locales
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/variables';

.sidebar {
  width: $menu_width;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  background: $main_color;
  box-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);

  text-align: center;

  display: flex;
  flex-direction: column;
  align-items: center;

  padding-bottom: 56px;

  @media all and (max-width: $breakpoint-sm) {
    display: none;
  }

  & > .logo {
    display: block;
    width: 100%;
    padding: 45px 0;

    &:hover {
      cursor: pointer;
    }

    & > img {
      width: 16px;
    }
  }

  & > .locale-selector {
    display: flex;
    flex-direction: column;
    margin-top: auto;

    & > a {
      color: $font_color;
      text-decoration: none;
      text-transform: uppercase;
      font-size: $f16;
      line-height: $f19;

      &.active {
        font-weight: bold;
      }

      & + a {
        margin-top: 20px;
      }
    }
  }
}
</style>
