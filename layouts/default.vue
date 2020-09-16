<template>
  <v-app dark>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-toolbar-title class="title" v-text="title" @click="$router.push('/')" />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    
  </v-app>
</template>

<script lang="ts">
import { Vue, Component, Watch } from 'nuxt-property-decorator'
@Component({})
export default class DefaultLayout extends Vue{
  clipped = false
  title = 'Youtube-dl-viewer'
   
}
</script>
<style lang="scss" scoped>
.title{
  cursor: pointer;
}
</style>