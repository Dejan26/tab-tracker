<template>
<v-layout light>
    <v-flex xs6>
  <panel title="Song Metadata">
    <v-alert
      outlined
    
    >
    <v-layout>
                <v-flex>
                    <div class="song-title">
                        {{song.title}}
                    </div>
                    <div class="song-artist">
                        {{song.artist}}
                    </div>
                    <div class="song-genre">
                        {{song.genre}}
                    </div>

                   
                </v-flex>

                <v-flex xs6>
                <img class="album-image" :src="song.albumImageUrl" />
                <br>
                {{song.album}}
                </v-flex>
            </v-layout>
            </v-alert>
    </panel>
   </v-flex>

   <v-flex  outlined xs6>
    <panel title="Tabs">
       <textarea 
      readonly

      v-model="song.tab"
    ></textarea>
    </panel>
   </v-flex>
   </v-layout>
</template>

<script>
import SongsService from '../services/SongsService'
import Panel from '@/components/Panel'


export default {
    components: {
        Panel
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
.border{
    border: 1px solid black;
}
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