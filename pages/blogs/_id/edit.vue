<template>
    <div>
    <div v-if="blog">
        Edit Post
    <v-text-field v-model="blog.title" label="Title"></v-text-field>
    <v-textarea v-model="blog.body" label="Body"></v-textarea>
    <v-btn @click="saveBtn">Save</v-btn>
    </div>
  </div>
</template>

<script>
import * as BlogsAPI from '@/utils/blogsAPI'
export default {
    name:'editPage',
    data(){
        return{
            blog: null
        }
    },
    async mounted(){
        console.log('ID', this.$route.params.id);
        const response = await BlogsAPI.show(this.$route.params.id)
        console.log('RESPONSE', response);
        this.blog = response.data
    },
    methods:{
        async saveBtn(){
            console.log('edit clicked', this.blog);
            const response = await BlogsAPI.update(
            this.blog.id, 
            this.blog.title, 
            this.blog.body
            )
            console.log('RESPONSE', response);
            this.$router.replace({name: 'blogs-id', params: {id: this.blog.id}})
        }
    }
}
</script>

<style>

</style>