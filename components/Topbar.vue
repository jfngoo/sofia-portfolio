<template>
  <div class="topbar">
    <nav>
      <nuxt-link
        :to="localePath('/')"
        :class="{ active: $route.name.includes('index___') }"
      >
        {{ $t('nav.work') }}
      </nuxt-link>

      <nuxt-link
        :to="localePath('/contact')"
        :class="{ active: $route.name.includes('contact___') }"
      >
        {{ $t('nav.contact') }}
      </nuxt-link>
    </nav>
    <div class="locale-selector">
      <nuxt-link
        v-for="locale in availableLocales.filter(l => l !== $i18n.locale)"
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

.topbar {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  background: $main_color;
  box-shadow: 0 0 70px rgba(43, 46, 69, 0.6);

  display: inline-flex;
  justify-content: space-between;
  align-items: center;

  z-index: 99;

  @media all and (min-width: $breakpoint-sm) {
    display: none;
  }

  nav {
    display: inline-flex;
    align-items: center;
    height: 72px;

    & > a {
      color: $font_color;
      text-decoration: none;
      padding: 26px;
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

  & > .locale-selector {
    display: inline-block;

    & > a {
      display: block;
      color: $font_color;
      text-decoration: none;
      text-transform: uppercase;
      font-size: $f16;
      line-height: $f19;
      flex: 1;
      padding: 26px;

      &.active {
        font-weight: bold;
      }
    }
  }
}
</style>
