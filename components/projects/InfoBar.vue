<template>
  <div class="infobar">
    <div class="project">
      <div class="title">
        {{ title }}
      </div>
      <div class="team">
        {{ team }}
      </div>
      <div class="subtitle">
        {{ date }}
      </div>
    </div>
    <div class="skills">
      <div class="title">
        {{ type }}
      </div>
      <div class="subtitle">
        {{ skills }}
      </div>
    </div>
    <div
      v-if="team"
      class="team"
    >
      <div class="title">
        {{ $t('a-project-with') }}
      </div>
      <div class="subtitle">
        {{ team }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'InfoBar',

  props: {
    title: {
      type: String,
      required: true
    },
    date: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: ''
    },
    skills: {
      type: String,
      default: ''
    },
    team: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss">
@import "~@/assets/style/variables";

.infobar {
  background: $main_color;
  min-height: 85px;
  width: 100%;
  padding: 15px 115px;

  display: flex;
  justify-content: space-between;
  align-items: center;

  @media screen and (max-width: $breakpoint-md) {
    padding: 15px 35px;
  }

  @media screen and (max-width: $breakpoint-sm) {
    padding: 15px 0;
  }

  & > .project, & > .skills, & > .team {
    margin: 0 20px;

    & > .team {
      display: none;
      font-weight: bold;

      @media screen and (max-width: $breakpoint-sm) {
        display: inline-block;
      }
    }

    & > .title {
      font-weight: bold;
    }

    & > .subtitle {
      font-weight: normal;
    }
  }

  & > .project, & > .skills {
    flex: 0.5;

    @media screen and (max-width: $breakpoint-md) {
      flex: 1;
    }
  }

  & > .project {
    & > .title {
      @media screen and (max-width: $breakpoint-sm) {
        display: none;
      }
    }
  }

  & > .skills {
    @media screen and (max-width: $breakpoint-sm) {
      text-align: right;
    }
  }

  & > .team {
    text-align: right;
    flex: 1;

    @media screen and (max-width: $breakpoint-md) {
      margin: 0;
    }

    @media screen and (max-width: $breakpoint-sm) {
      display: none;
    }
  }
}
</style>
