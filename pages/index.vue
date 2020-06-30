<template>
  <div class="app">
    <Sidebar />
    <div class="intro-container">
      <Intro />
    </div>
  </div>
</template>

<script>
import Vue from 'vue'

export default Vue.extend({})
</script>

<style lang="scss">

@import '../assets/style/fonts';
@import '../assets/style/variables';

.app {
  background: $grey4;
  font-family: $barlow;
  padding-left: $menu_width;
}

.intro-container {
  min-height: 100vh;
  display: flex;
  align-items: flex-end;
  padding-bottom: 115px;
  padding-left: 111px;
}
</style>
