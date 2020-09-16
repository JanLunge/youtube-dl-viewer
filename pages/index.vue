<template>
  <v-layout column justify-center align-center>
    <v-row>
      <VideoPreview v-for="video in pages" :key="video.path" :video="video"/>
    </v-row>
  </v-layout>
</template>

<script lang="ts">
import VideoPreview from "~/components/videoPreview.vue";
import { Vue, Component, Watch } from 'nuxt-property-decorator'

@Component({components: {
    VideoPreview
  }})
export default class VideoList extends Vue {
  
  async asyncData(context:any) {
    const pages = await context.$content("videos").fetch();
    return {
      pages
    };
  }

};
</script>
<style lang="scss" scoped>

</style>