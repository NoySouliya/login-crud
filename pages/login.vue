<template>
  <div>
    <v-text-field v-model="email" label="Email"></v-text-field>
    <v-text-field v-model="password" label="Password" type="password"></v-text-field>
    <v-btn @click="loginClicked"> Login </v-btn>
  </div>
</template>

<script>
export default {
  layout: 'session',
  data(){
    return{
      email: '',
      password: '',
    }
  },
  methods:{
    async loginClicked(){
      try {
        const response = await this.$auth.loginWith('local',{ 
          data: {user: {email: this.email, password: this.password }} })
        console.log(response);
        if (response.data.success){
          this.$router.replace({ name: 'blogs' })
        }
      }catch (err) {
        console.log(err);
      }
    }
  }
}
</script>

<style>

</style>