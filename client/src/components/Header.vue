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
 
        <v-toolbar-items>
      <v-btn  @click="navigateTo({name: 'Songs'})">
        Browse
      </v-btn>
        </v-toolbar-items>

        <v-toolbar-items>
        
      <v-btn v-if="!$store.state.isUserLoggedIn" @click="navigateTo({name: 'Register'})">
         Sign Up
      </v-btn>
    
      <v-btn v-if="!$store.state.isUserLoggedIn" @click="navigateTo({name: 'Login'})">
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
    navigateTo(route){
this.$router.push(route)
    },
    logout(){
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({name: 'root'})
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