<template>
  <div class="nextbar">
    <div class="previous">
      <div class="thread">
        <div class="bar" />
        <div class="circle" />
      </div>
      <div class="text">
        <div class="label">
          Previous
        </div>
        <div class="title">
          Orianna
        </div>
      </div>
    </div>

    <div class="next">
      <div class="text">
        <div class="label">
          Next
        </div>
        <div class="title">
          Improvize
        </div>
      </div>

      <div class="thread">
        <div class="circle" />
        <div class="bar" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NextBar'
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
