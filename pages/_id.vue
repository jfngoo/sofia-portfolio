<template>
  <div class="project">
    <Sidebar />
    <div class="project-container">
      <div
        class="banner project-banner"
        :style="{ backgroundImage: `url('${require(`../assets/img/posters/${project.id}.jpg`)}')` }"
      >
        <div class="text">
          <h1 class="title">
            {{ project.title }}
          </h1>
          <h2 class="subtitle">
            {{ project.subtitle }}
          </h2>
        </div>
      </div>
    </div>
    <InfoBar
      :title="project.title"
      :date="project.date"
      :type="project.type"
      :skills="project.skills"
      :team="project.team"
    />
    <div class="container">
      <div class="row">
        <TextBlock
          subtitle="CONTEXT"
          title="Voice assistant & privacy"
          :text="'<p>Getting informations quickly, control several house equipments, call without using your hands… It’s not just a fantasy, and it was already possible to access those services on several voice assistant.</p><p>But Orange is now positioned in the market, thanks to Djingo, focusing on the privacy of its clients data. The \'Bible\' (reference doc / fondamental characteristics of Djingo), created by Frederic Mit, Elena Tosi Brandi & Pascal Taillard, ensures the coherence of that principle amongst others.</p>'"
        />
      </div>
      <div class="row">
        <VideoEmbedBlock
          host="facebook"
          url="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2FOrange.France%2Fvideos%2F795742717528294%2F&show_text=0&width=476"
        />
      </div>
      <div class="row">
        <TextBlock
          subtitle="HOW DOES IT WORK?"
          title="A well oiled machine"
          :text="'<p>Djingo evolved a lot across those two years of development, between Orange’s desire to make a high-quality user-centric product and the reality of technology and marketing that rose along the way.</p><p>I joined one of the Design team in january 2019, and the months that went by allowed me to work on many aspects of that voice assistant.</p><br><p>To stay focused, different teams were created, working Agile and organising weekly meetings, which gave us the opportunity to see how far along everyone was (and anticipate needs).</p>'"
        />
        <ImageBlock
          :id-project="project.id"
          image="image-1.png"
        />
      </div>
      <div class="row fullsize">
        <ImageRow
          :id-project="project.id"
          image="image-2.jpg"
        />
      </div>
      <div class="row">
        <TextBlock
          subtitle="PROJECT"
          title="A rich experience"
          :text="'<p>My main mission has been to help Thomas Lauby and share the amount of work on the mobile app’s design:</p><ul><li>Question UX & review/make UI for existing services;</li><li>Anticipate other features, pages, screens…;</li><li>Answer to PO’s delivery needs;</li><li>Apply Orange’s Design System...</li></ul><br><p>I also took part in various workshops, as a participant and as organiser:</p><ul><li>Error messages (in-app & vocal);</li><li>Management of multiple accounts / profiles (long term vision, outside of MVP);</li><li>Orange TV skill inside Djingo’s global ecosystem...</li></ul></ul>'"
        />
        <TextBlock
          subtitle=""
          title=""
          :text="'<p>Finally, I had the opportunity to do some CUX for a skill that should be released in 2020.</p><br><p>My work on Djingo isn’t quite over yet since I’m currently working on Djingo’s animacy (visual expressivity of Djingo cross-platform)</p>'"
        />
      </div>
      <div class="row">
        <ImageBlock
          type="2col"
          :id-project="project.id"
          image="image-3.jpg"
        />
      </div>
      <div class="row">
        <ImageBlock
          type="2col"
          :id-project="project.id"
          image="image-4.jpg"
        />
      </div>
    </div>
  </div>
</template>

<script>
import TextBlock from '../components/projects/TextBlock'
import ImageBlock from '../components/projects/ImageBlock'
export default {
  name: 'Project',
  components: { ImageBlock, TextBlock },
  computed: {
    project () {
      return this.$i18n.messages[this.$i18n.locale].projects.find(x => x.id === this.$route.params.id)
    }
  },

  head () {
    return {
      title: `Sofia Boggio - ${this.project.title}`,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: this.project.subtitle }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/fonts';
@import '../assets/style/variables';
@import '../assets/style/typo';

.project {
  background: $grey4;
  font-family: $barlow;
  padding-left: $menu_width;
  padding-bottom: 60px;
  color: $font_color;

  @media all and (max-width: $breakpoint-sm) {
    padding: 0;
  }

  .banner {
    width: 100%;
    height: 530px;
    background: center center no-repeat;
    background-size: cover;
    display: flex;
    align-items: center;
  }

  & > .container {
    padding: 80px 0;

    .row {
      display: flex;
      padding: 0 115px;

      &.fullsize {
        padding: 0;
      }

      & > .block + .block {
        margin-left: 25px;
      }

      & + .row {
        margin-top: 104px;
      }
    }
  }
}
</style>
