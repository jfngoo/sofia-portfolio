<template>
  <div class="block text-block">
    <h3 class="subtitle">
      Context
    </h3>
    <h2 class="title">
      Voice assistant & privacy
    </h2>
    <div class="text">
      <p>
        Getting informations quickly, control several house equipments, call without using your hands… It’s not just a fantasy, and it was already possible to access those services on several voice assistant.
      </p>
      <p>
        But Orange is now positioned in the market, thanks to Djingo, focusing on the privacy of its clients data. The "Bible" (reference doc / fondamental characteristics of Djingo), created by Frederic Mit, Elena Tosi Brandi & Pascal Taillard, ensures the coherence of that principle amongst others.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TextBlock'
}
</script>

<style lang="scss">
@import "~@/assets/style/variables";

.text-block {
  .subtitle {
    font-size: $f20;
    line-height: $f26;
    text-transform: uppercase;
    font-weight: normal;
  }

  .title {
    font-family: $zilla_slab;
    font-size: $f56;
    line-height: $f48;
    margin: 24px 0;
  }

  .text p {
    text-indent: 30px;
    font-size: $f18;
    line-height: $f28;
  }
}

</style>
