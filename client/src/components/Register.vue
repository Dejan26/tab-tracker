<template>
  
    <v-layout column>
      <v-flex xs6 offset-xs3>
        <panel title="Register">

      <form name="tab-tracker-form" autocomplete="off">
    <v-text-field
      label="Email"
      
      v-model="email"
    ></v-text-field>
    
    <br>
    <v-text-field
      label="Password"
      type="password"
      v-model="password"
      autocomplete="new-password"
    ></v-text-field>
    </form>
    <br>
    <div class="error" v-html="error"></div>
    <br>
    <v-btn class="cyan" @click="register" >Register</v-btn>
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
async register(){
  try {
   const response = await AuthenticationService.register({
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