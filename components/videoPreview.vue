<template>
<v-card class="ma-4 video" >
        <div class=""  @click="goToVideo(video)" >
          <v-img
            :width="320"
            :src="thumbnailSrc"
          />
<div class="description pa-4">
          <p class="font-weight-bold">{{ video.title }}</p>
          <span class="grey--text">{{ video.uploader }}</span><br>
          <span class="grey--text">{{ video.view_count }} views • {{ uploadDate }}</span>
          </div>
        </div>
      </v-card>
</template>
<script>
import Vue from 'vue'
export default Vue.extend({
    props:{
        video: Object
    },
    methods:{
         goToVideo(video){
            this.$router.push('/v/' + video.path.split('/')[2])
        },
        
    },
    computed:{
        thumbnailSrc(){
            const lastThumbnail = this.video.thumbnails[this.video.thumbnails.length-1]
            const fileExt = lastThumbnail.url.split('/')[lastThumbnail.url.split('/').length-1].split('.')[1];
            return '/v/' + this.video.path.split('/')[2].split('.')[0] + '.'+fileExt;
        },
        uploadDate(){
            return this.video.upload_date.slice(0,4)+'/'+this.video.upload_date.slice(4,6)+'/'+this.video.upload_date.slice(6,8)
        }
    }
})
</script>