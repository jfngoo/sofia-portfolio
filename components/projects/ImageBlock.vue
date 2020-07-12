<template>
  <div
    :class="{ full: type === '2col' }"
    class="image-block"
  >
    <img
      :src="require(`~/assets/img/projects/${idProject}/${image}`)"
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
      required: true
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

  & > img {
    max-width: 100%;
  }

  &.full {
    flex: 1;

    & > img {
      width: 100%;
    }
  }
}

.fullsize {
  & > .block  {
    flex: 1;
    & > .image-block {
      & > img {
        width: 100%;
      }
    }
  }
}

</style>
