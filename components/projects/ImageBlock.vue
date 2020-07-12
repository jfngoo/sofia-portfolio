<template>
  <div class="block image-block">
    <img
      :src="require('../../assets/img/projects/djingo/image-1.png')"
      :alt="alt"
    >
  </div>
</template>

<script>
export default {
  name: 'TextBlock',
  props: {
    idProject: {
      type: String,
      default: ''
    },
    image: {
      type: String,
      default: ''
    },
    alt: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss">
@import "~@/assets/style/variables";

.image-block {
  text-align: center;
}

</style>
