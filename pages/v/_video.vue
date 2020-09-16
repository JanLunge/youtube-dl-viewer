<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline">
          {{ page.title }}
        </v-card-title>
        <v-card-text>
          <video :src="'/v/' + page._filename"></video>
          <p>
            Vuetify is a progressive Material Design component framework for
            Vue.js. It was designed to empower developers to create amazing
            applications.
          </p>
          <p
            v-for="(paragraph, index) in page.description.split('\n')"
            :key="index"
          >
            {{ paragraph }}
          </p>
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
}
</script>
