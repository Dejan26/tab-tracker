<template>
<v-card

    color="grey lighten-4"
    flat
    
    tile
    
  >
    <v-toolbar  dense>
        
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>
        <span class="home" @click="navigateTo({name: 'root'})">
        Tab Tracker
        </span>
        </v-toolbar-title>

      <v-spacer></v-spacer>

        
        
        
        
        <!-- <v-toolbar-items>
      <v-btn >
        Browse
      </v-btn>
        </v-toolbar-items> -->

        <v-toolbar-items>
        
      <v-btn @click="navigateTo({name: 'Register'})">
         Sign Up
      </v-btn>
    
        </v-toolbar-items>

<v-toolbar-items>
      <v-btn @click="navigateTo({name: 'Login'})">
        Login
      </v-btn>
</v-toolbar-items>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
  </v-card>
 
</template>

<script>
export default {
methods:{
    navigateTo(route){
this.$router.push(route)
    }
}
}
</script>

<style scoped>
.home{
    cursor: pointer;
}
.home:hover{
    color: darkslateblueW;
}
.re{
    color:red
}

</style>