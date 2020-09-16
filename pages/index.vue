<template>
  <v-layout column justify-center align-center>
    <v-row>
      <videoPreview v-for="video in pages" :key="video.path" :video="video"/>
    </v-row>
  </v-layout>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";
import videoPreview from "~/components/videoPreview.vue";
export default {
  components: {
    Logo,
    VuetifyLogo,
    videoPreview
  },
  async asyncData({ $content }) {
    const pages = await $content("videos").fetch();

    return {
      pages
    };
  },

};
</script>
<style lang="scss" scoped>
.video{
  width: 320px;
  cursor: pointer;
  overflow: hidden;
}
</style>