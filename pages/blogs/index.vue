<template>
  <div>
      blogs !!!! Required login
      <v-btn :to="{name: 'blogs-newOne'}">New Blog</v-btn>
    <v-card v-for="blog in blogs" :key='blog.id'
    class="mx-auto"
    max-width="344"
    style="margin-top: 10px"
  >
    <v-card-text>
      <p class="text-h4 text--primary">
        {{ blog.title }}
      </p>
    <div class="text--primary">
      blog id: {{blog.id}}
      </div>
    </v-card-text>
    <v-card-actions>
      <v-btn
        text
        color="teal accent-4"
        :to="{ name: 'blogs-id', params: { id: blog.id } }"
      >
        Learn More
      </v-btn>
    </v-card-actions>
      </v-card>
  </div>
</template>

<script>
import * as BlogsAPI from '@/utils/blogsAPI'
export default {
  name:'IndexLogin',
  middleware: 'auth',
  data(){
    return{
      blogs: []
    }
  },
  async mounted(){
    const response = await BlogsAPI.index()
    console.log('RESPONSE',response);
    this.blogs = response.data
  }
}
</script>

<style>

</style>