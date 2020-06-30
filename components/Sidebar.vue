<template>
  <div class="sidebar" />
</template>

<script>
export default {
  name: 'Sidebar'
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
}
</style>
