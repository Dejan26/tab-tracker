<template>
<div>
<v-layout>
    <v-flex xs6>
        <song-metadata :song="song" />
   </v-flex>

<v-flex xs6 class="ml-2">
    <you-tube :youtubeId="song.youtubeId" />
</v-flex>
</v-layout>

<v-layout class="mt-2">
    <v-flex xs6>
       <tab :song="song" />
   </v-flex>

<v-flex xs6 class="ml-2 ">
   <lyrics :song="song" />
</v-flex>
</v-layout>



   </div>
</template>

<script>
import Lyrics from './Lyrics'
import Tab from './Tab'
import SongsService from '../../services/SongsService'
import SongMetadata from './SongMetadata.vue'
import YouTube from './YouTube'



export default {
    components: {
    SongMetadata,
    YouTube,
    Lyrics,
    Tab
},
    data () {
        return {
            song: {}
        }
    },
async mounted () {
    const songId = this.$store.state.route.params.songId
    this.song = (await SongsService.show(songId)).data
    console.log(this.song)
}
}
</script>

<style scoped>


textarea{
    width: 100%;
    font-family: monospace;
    border: none;
    height: 600px;
    border-style: none;
    border-color: transparent;
    overflow: auto;
    padding: 20px;
    
}
</style>