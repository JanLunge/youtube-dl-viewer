<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-text>
          <video class="video-player mb-3" controls :src="'/v/' + page.path.split('/')[2].split('.')[0]+'.'+videoExtension"></video>
          <h2 class="pb-3 white--text">{{page.title}}</h2>
          <p>{{page.view_count}} views • {{uploadDate}}</p>
          <v-divider class="pb-4"/>
          <a :href="page.uploader_url" target="_blank" class="font-weight-bold white--text">{{page.uploader}}</a>
          <div class="mt-3">

          <p
            v-for="(paragraph, index) in page.description.split('\n')"
            :key="index"
          >
            {{ paragraph }}
          </p>
          </div>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'
@Component({})
export default class VideoDetail extends Vue {
  async asyncData(context: any) {
    const page = await context
      .$content('videos/' + context.params.video)
      .fetch()
    return {
      page,
    }
  }
  get videoExtension(){
    return 'mp4'

  }
    get uploadDate() {
    return (
      this.page.upload_date.slice(0, 4) +
      '/' +
      this.page.upload_date.slice(4, 6) +
      '/' +
      this.page.upload_date.slice(6, 8)
    )
  }
}
</script>
<style lang="scss" scoped>
.video-player{
  width: 100%;
}
</style>
