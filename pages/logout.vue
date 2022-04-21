<template>
  <v-btn @click="logoutClick">Logout</v-btn>
</template>

<script>
export default {
    methods:{
      logoutClick(){
        this.$nuxt.$auth.logout()
      }
    }
}
</script>

<style>

</style>