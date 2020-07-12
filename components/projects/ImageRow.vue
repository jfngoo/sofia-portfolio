<template>
  <div class="block image-row">
    <img
      :src="require(`../../assets/img/projects/${idProject}/${image}`)"
      :alt="alt"
    >
  </div>
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

.image-row {
  text-align: center;
  flex: 1;

  & > img {
    width: 100%;
  }
}

</style>
