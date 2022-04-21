<template>
  <div>NEW BLOG
    <v-text-field v-model="title" label="Title"></v-text-field>
    <v-textarea v-model="body" label="Body"></v-textarea>
    <v-btn @click="createBtn">Create</v-btn>
  </div>
</template>

<script>
import * as BlogsAPI from '@/utils/blogsAPI'
export default {
    data(){
        return{
            title: '',
            body: ''
        }
    },
    methods:{
        async createBtn(){
            if (this.title.length === 0){
                return
            }
            const response = await BlogsAPI.create(this.title, this.body)
            console.log('RESPONSE', response)
            this.$router.replace({name: 'blogs-id', 
            params: {
                id: response.data.id
                }
            })
        }
    }
}
</script>

<style>

</style>