<template>
    <v-layout column>
      <v-flex xs6 offset-xs3>
        <panel title="Login">
    <v-text-field
      label="Email"  
      v-model="email"
    ></v-text-field> 
    <br>
    <v-text-field
      label="Password"
      type="password"
      v-model="password"
    ></v-text-field>
    <br>
    <div class="error" v-html="error"></div>
    <br>
    <v-btn class="cyan" @click="login" >Login</v-btn>
  </panel>
  </v-flex>
    </v-layout>

  
    
  
</template>

<script>
import AuthenticationService from '../services/AuthenticationService'


export default {

    
data(){
    return {
        email: '',
        password: '',
        error: null
    }
},
methods:{
async login(){
  try {
   const response = await AuthenticationService.login({
    email: this.email,
    password: this.password
   })
   this.$router.push({name: 'Songs'})
   this.$store.dispatch('setToken', response.data.token)
   this.$store.dispatch('setUser', response.data.user)
  
    
   
   
   } catch(error){
    this.error = error.response.data.error
   }
   
}
    }
}
</script>

<style scoped>
.error{
  color:red
}
.layout.column>.flex{
  margin:0 50px;
  max-width: 80%;
}
</style>