<template>
  <div class="about-and-contact">
    <Topbar />
    <Sidebar />
    <About />
  </div>
</template>

<script>
export default {
  name: 'AboutAndContact'
}
</script>

<style lang="scss" scoped>
@import '../assets/style/fonts';
@import '../assets/style/variables';
@import '../assets/style/typo';

.about-and-contact {
  background: $grey4;
  font-family: $barlow;
  color: $font_color;
  padding: 146px 0 296px $menu_width;

  @media all and (max-width: $breakpoint-md) {
    padding: 146px 0 100px $menu_width;
  }

  @media all and (max-width: $breakpoint-sm) {
    padding: 0;
  }
}
</style>
