<template>
  <div class="sidebar">
    <nuxt-link
      :to="getUrl($i18n.locale)"
      class="logo"
    >
      <img
        src="../assets/img/logo.png"
        alt="Logo"
      >
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'Sidebar',

  methods: {
    getUrl (locale) {
      return locale !== 'fr' ? `/${locale}/` : '/'
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

  text-align: center;

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
}
</style>
