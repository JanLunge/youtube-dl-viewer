<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
     
      <v-card>
        <v-card-title class="headline">
         {{page.title}}
        </v-card-title>
        <v-card-text>
          <video :src="'/v/'+page._filename"></video>
          <p>Vuetify is a progressive Material Design component framework for Vue.js. It was designed to empower developers to create amazing applications.</p>
          <p v-for="paragraph in page.description.split('\n')">
            {{paragraph}}
          
          </p>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  async asyncData (context) {
    console.log(context)
    const page = await context.$content("videos/"+context.params.video).fetch()

    return {
      page
    }
  }
}
</script>
