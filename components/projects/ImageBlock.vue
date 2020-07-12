<template>
  <div
    :class="{ full: type === '2col' }"
    class="block image-block"
  >
    <img
      :style="{ maxHeight: maxHeight !== 0 ? `${maxHeight}px` : 'auto' }"
      :src="require(`../../assets/img/projects/${idProject}/${image}`)"
      :alt="alt"
    >
  </div>
</template>

<script>
export default {
  name: 'ImageBlock',
  props: {
    type: {
      type: String,
      default: ''
    },
    idProject: {
      type: String,
      default: ''
    },
    image: {
      type: String,
      default: ''
    },
    maxHeight: {
      type: Number,
      default: 0
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
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 0.5;

  &.full {
    flex: 1;

    & > img {
      width: 100%;
    }
  }
}

</style>
