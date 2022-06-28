<template>
  
    <v-layout column>
      <v-flex xs6 offset-xs3>
        <panel title="Songs">
            <router-link  slot="action" :to="{name: 'songs-create'}">
                <v-btn  class="info" fab>
          add
        </v-btn>
        </router-link>
            <div v-for="song in songs" :key="song.id"  class="song">

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

                    <v-btn
                      dark
                      class="cyan"
                      :to="{
                       name: 'song', 
                       params: {
                       songId: song.id
                          }
                       }">
                             View
                    </v-btn>
                </v-flex>

                <v-flex xs6>
                <img class="album-image" :src="song.albumImageUrl" />
                </v-flex>
            </v-layout>
               

            </div>
        </panel>
  </v-flex>
    </v-layout>

</template>

<script>
import SongsService from '@/services/SongsService'
export default {

data(){
    return {
        songs: []
    }
},
watch: {
    '$route.query.search': {
        immediate: true,
       async handler (value) {
            this.songs = (await SongsService.index(value)).data
        }
    }
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