<template>
  <v-layout column justify-center align-center>
    <v-row>
      <v-card class="ma-4" v-for="video in pages" :key="video.path">
        <div class="video"  @click="goToVideo(video)" >
          <v-img
            :width="320"
            :src="'/v/' + video.path.split('/')[2].split('.')[0] + '.'+video.thumbnails[video.thumbnails.length-1].url.split('/')[video.thumbnails[video.thumbnails.length-1].url.split('/').length-1].split('.')[1]"
          />
<div class="description pa-4">
          <p class="font-weight-bold">{{ video.title }}</p>
          <span class="grey--text">{{ video.uploader }}</span><br>
          <span class="grey--text">{{ video.view_count }} views • {{ uploaddate(video) }}</span>
          </div>
        </div>
      </v-card>
    </v-row>
  </v-layout>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  async asyncData({ $content }) {
    const pages = await $content("videos").fetch();

    return {
      pages
    };
  },
methods:{
goToVideo(video){
this.$router.push('/v/' + video.path.split('/')[2])
},
  uploaddate(video){
    return video.upload_date.slice(0,4)+'/'+video.upload_date.slice(4,6)+'/'+video.upload_date.slice(6,8)
  }
}
};
</script>
<style lang="scss" scoped>
.video{
  width: 320px;
  cursor: pointer;
}
</style>