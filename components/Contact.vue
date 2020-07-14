<template>
  <div class="contact">
    <h2 class="title">
      {{ $t('contact.title') }}
    </h2>
    <div class="contact-me">
      {{ $t('contact.contact-me') }}
    </div>
    <div class="email">
      {{ $t('contact.email') }}
    </div>
    <div class="follow">
      <div class="text">
        {{ $t('contact.follow') }}
      </div>
      <div class="social">
        <a
          v-for="media in medias"
          :key="media.url"
          :href="media.url"
          class="link"
        >
          <img
            :src="require(`../assets/img/social/${media.host}.svg`)"
            :alt="`${media.host} link`"
          >
        </a>
      </div>
    </div>
    <div class="thanks">
      <i18n
        path="contact.thanks.message"
        tag="label"
        for="contact.thanks.display"
      >
        <a
          class="link"
          :href="$t('contact.thanks.link')"
          target="_blank">
          {{ $t('contact.thanks.display') }}
        </a>
      </i18n>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Contact',

  computed: {
    medias () {
      return this.$i18n.messages[this.$i18n.locale].contact.social
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/variables";

.contact {
  font-size: $f18;
  line-height: $f28;

  @media screen and (max-width: $breakpoint-sm) {
    padding: 25px 45px;
  }

  & > .title {
    font-family: $zilla_slab;
    font-size: $f48;
    line-height: $f44;
    margin-bottom: 48px;
    margin-top: 45px;

    @media screen and (max-width: $breakpoint-sm) {
      font-size: $f48;
      line-height: $f44;
    }
  }

  & > .email {
    font-weight: bold;
  }

  & > .follow {
    margin-top: 48px;

    & > .social {
      display: flex;
      margin-top: 10px;

      & > .link {
        width: 34px;
        height: 34px;
        color: $font_color;

        & > img {
          width: 100%;
          height: 100%;
        }

        & + .link {
          margin-left: 24px;
        }
      }
    }
  }

  & > .thanks {
    margin-top: 48px;
  }

  a.link {
    color: $font_color;
  }
}
</style>
