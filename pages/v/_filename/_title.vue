<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-text>
          <video
            class="video-player mb-3"
            controls
            :src="
             videoUrl
            "
          ></video>
          <h2 class="pb-3 white--text">{{ video.title }}</h2>
          <p>{{ video.view_count }} views • {{ uploadDate }}</p>
          <v-divider class="pb-4" />
          <a
            :href="video.uploader_url"
            target="_blank"
            class="font-weight-bold white--text"
            >{{ video.uploader }}</a
          >
          <div class="mt-3">
            <p
              v-for="(paragraph, index) in video.description.split('\n')"
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
  video: any
  async asyncData(context: any) {
    const buffer = require('buffer').Buffer
    const video = await context.$content(
        'videos/' +
          buffer.from(context.params.filename, 'base64').toString('binary')
      )
      .fetch()
    return {
      video,
    }
  }

  get videoExtension() {
    return 'mp4'
  }

  get videoUrl() {
    console.log(this.video)
    const filename = this.video.path.split('/')[2]
    const filenameWithoutExtension = filename.replace(/\.[^/.]+$/, '')
    return `/v/${filenameWithoutExtension}.${this.videoExtension}`
  }

  get uploadDate() {
    return (
      this.video.upload_date.slice(0, 4) +
      '/' +
      this.video.upload_date.slice(4, 6) +
      '/' +
      this.video.upload_date.slice(6, 8)
    )
  }
}
</script>
<style lang="scss" scoped>
.video-player {
  width: 100%;
}
</style>
