<template>
<v-card
    color="grey lighten-4"
    flat
    tile 
  >
    <v-toolbar  dense>
        
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title class="mr-4">
        <router-link class="home"  tag="span" :to="{name: 'Songs'}">
        Tab Tracker
        </router-link>
        </v-toolbar-title>

      <v-spacer></v-spacer>
 
        <v-toolbar-items>
      <v-btn flat dark :to="{name:'Songs'}">
        Browse
      </v-btn>
        </v-toolbar-items>

        <v-toolbar-items>
        
      <v-btn v-if="!$store.state.isUserLoggedIn" :to="{name: 'Register'}">
         Sign Up
      </v-btn>
    
      <v-btn v-if="!$store.state.isUserLoggedIn" :to="{name: 'Login'}">
        Login
      </v-btn>

      <v-btn v-if="$store.state.isUserLoggedIn" @click="logout">
        Log Out
      </v-btn>
</v-toolbar-items>

      
    </v-toolbar>
  </v-card>
 
</template>

<script>
export default {
methods:{
    
    logout(){
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({name: 'Songs'})
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