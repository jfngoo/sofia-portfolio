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

  @media all and (max-width: $breakpoint-sm) {
    margin-top: 150px;

    & + .image-block {
      margin-top: 0;
    }
  }

  & > img {
    max-width: 100%;
  }

  &.full {
    flex: 1;

    @media all and (max-width: $breakpoint-sm) {
      margin-top: 0;
    }

    & > img {
      width: 100%;
    }
  }
}

.fullsize {
  & > .block  {
    flex: 1;

    & > .image-block {

      @media all and (max-width: $breakpoint-sm) {
        margin-top: 0;
      }

      & > img {
        width: 100%;
      }
    }
  }
}

</style>
