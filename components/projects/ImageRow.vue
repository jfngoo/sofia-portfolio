<template>
  <div
    class="image-row"
    :style="{ backgroundImage: `url('${require(`~/assets/img/projects/${idProject}/${image}`)}')` }"
  />
</template>

<script>
export default {
  name: 'ImageRow',
  props: {
    idProject: {
      type: String,
      default: ''
    },
    image: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss">
@import "~@/assets/style/variables";

.image-row {
  height: 500px;
  background: center center no-repeat;
  background-size: cover;
}

</style>
