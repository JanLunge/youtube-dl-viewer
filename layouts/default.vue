<template>
  <v-app dark>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-toolbar-title
        class="title"
        @click="$router.push('/')"
        v-text="title"
      />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'
@Component({})
export default class DefaultLayout extends Vue {
  clipped = false
  title = 'Youtube-dl-viewer'
}
</script>
<style lang="scss" scoped>
.title {
  cursor: pointer;
}
</style>
