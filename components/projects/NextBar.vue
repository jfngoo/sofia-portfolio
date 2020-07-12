<template>
  <div class="nextbar">
    <nuxt-link
      :to="getUrl(previous.id)"
      class="previous"
    >
      <div class="thread">
        <div class="bar" />
        <div class="circle" />
      </div>
      <div class="text">
        <div class="label">
          {{ $t('previous') }}
        </div>
        <div class="title">
          {{ previous.title }}
        </div>
      </div>
    </nuxt-link>

    <nuxt-link
      :to="getUrl(next.id)"
      class="next"
    >
      <div class="text">
        <div class="label">
          {{ $t('next') }}
        </div>
        <div class="title">
          {{ next.title }}
        </div>
      </div>

      <div class="thread">
        <div class="circle" />
        <div class="bar" />
      </div>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'NextBar',

  props: {
    previous: {
      type: Object,
      required: true
    },
    next: {
      type: Object,
      required: true
    }
  },

  methods: {
    getUrl (projectId) {
      return this.$i18n.locale !== 'fr' ? `/${this.$i18n.locale}/${projectId}` : `/${projectId}`
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/variables";
$horizontalPadding: 115px;

.nextbar {
  background: $main_color;
  min-height: 85px;
  width: 100%;

  display: flex;
  justify-content: space-between;
  align-items: center;

  @media screen and (max-width: $breakpoint-sm) {
    justify-content: flex-end;
  }

  & > .previous, & > .next {
    display: flex;
    justify-content: center;
    align-items: center;
    color: $font_color;
    text-decoration: none;

    & > .text {
      padding: 30px;

      & > .label {
        font-family: $zilla_slab;
        font-size: $f36;
        line-height: $f48;
      }

      & > .title {
        font-size: $f20;
        line-height: $f26;
      }

      &:hover {
        cursor: pointer;
      }
    }

    & > .thread {
      display: flex;
      justify-content: center;
      align-items: center;

      .circle {
        background: $font_color;
        height: 10px;
        width: 10px;
        border-radius: 50%;
        overflow: hidden;
      }

      .bar {
        background: $font_color;
        height: 2px;
        width: calc(#{$horizontalPadding} - 30px);
        overflow: hidden;
      }
    }
  }

  & > .next {
    text-align: right;
  }

  & > .previous {
    @media screen and (max-width: $breakpoint-sm) {
      display: none;
    }
  }
}
</style>
