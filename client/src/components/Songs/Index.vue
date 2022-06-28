<template>
  
    <v-layout column>
      <v-flex xs6 offset-xs3>
            <songs-search-panel class="mt-2" />
            <songs-panel />

                </v-flex>
            </v-layout>
               
</template>

<script>
import SongsPanel from './SongsPanel'
import SongsSearchPanel from './SongsSearchPanel'
import SongsService from '@/services/SongsService'

export default {
components: {
    
    SongsPanel,
    SongsSearchPanel
},
data(){
    return {
        songs: []
    }
},
async mounted(){
this.songs = (await SongsService.index()).data
}
}
</script>

<style scoped>
.song {
    padding: 20px;
    height: 330px;
    overflow: hidden;
}
.song-title {
    font-size: 30px;
}
.song-artist {
    font-size: 24px;
}
.song-genre {
    font-size: 18px;
}
</style>