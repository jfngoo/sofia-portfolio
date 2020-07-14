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
    <nav>
      <nuxt-link
        :to="localePath('/contact')"
        :class="{ active: $route.name.includes('contact___') }"
      >
        {{ $t('contact') }}
      </nuxt-link>

      <nuxt-link
        :to="localePath({ path: '/', hash: 'projects' })"
        :class="{ active: $route.name.includes('index___') }"
      >
        {{ $t('work') }}
      </nuxt-link>
    </nav>
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
  justify-content: flex-end;

  padding-bottom: 56px;

  @media all and (max-width: $breakpoint-sm) {
    display: none;
  }

  nav {
    display: flex;
    transform: rotate(-90deg);
    margin-bottom: 160px;

    @media all and (max-height: 600px) {
      margin-bottom: 80px;
    }

    & > a {
      color: $font_color;
      text-decoration: none;
      padding: calc(#{$menu_width}/2 - 10px) 28px;
      font-size: $f16;
      line-height: $f19;

      &:hover {
        cursor: pointer;
      }

      &.active {
        font-weight: bold;
      }
    }
  }

  & > .logo {
    display: block;
    width: 100%;
    padding: 45px 0;
    margin-bottom: auto;

    &:hover {
      cursor: pointer;
    }

    & > img {
      width: 16px;
    }
  }

  & > .locale-selector {
    width: 100%;
    display: flex;
    flex-direction: column;

    & > a {
      display: block;
      color: $font_color;
      text-decoration: none;
      text-transform: uppercase;
      font-size: $f16;
      line-height: $f19;
      padding: 10px 0;
      flex: 1;

      &.active {
        font-weight: bold;
      }
    }
  }
}
</style>
