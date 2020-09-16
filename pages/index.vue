<template>
  <v-layout column justify-center align-center>
    <v-row>
      <videoPreview v-for="video in pages" :key="video.path" :video="video"/>
    </v-row>
  </v-layout>
</template>

<script>
import videoPreview from "~/components/videoPreview.vue";
export default {
  components: {
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