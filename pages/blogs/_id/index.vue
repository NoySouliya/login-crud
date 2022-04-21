<template>
<div>
  <div  v-if='blog'>
      <v-btn :to="{ name: 'blogs-id-edit', params: {id: this.$route.params.id} }">
          Edit
      </v-btn>
          <v-btn
      depressed
      color="error"
      @click="deleteClick"
    >
      Delete
    </v-btn>
      <h1>
          {{blog.title}}
      </h1>
      <p>{{blog.body}}</p>
  </div>
  </div>
</template>

<script>
import * as BlogsAPI from '@/utils/blogsAPI'
export default {
    name:'IndexId',
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
        async deleteClick(){
            const response = await BlogsAPI.destroy(this.$route.params.id)
            console.log('RESPPONSE', response);
            this.$router.replace({name: 'blogs'})
        }
    }
}
</script>

<style>

</style>