<template>
  <panel title="Song Metadata">
    <v-alert
      outlined
    >
    <v-layout>
                <v-flex xs6>
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
                       name: 'song-edit', 
                       params: {
                       songId: song.id
                          }
                       }">
                             Edit
                    </v-btn>
                    
                   
                </v-flex>

                <v-flex xs6>
                <img class="album-image" :src="song.albumImageUrl" />
                <br>
                {{song.album}}
                </v-flex>
            </v-layout>
            </v-alert>
    </panel>
</template>

<script>

export default {
 props: [
    'song'
    
 ]
 
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