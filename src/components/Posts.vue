<template>
<div class="container my-3"> 
<div class="row row-cols-1 row-cols-md-4 g-4">
  <div v-for="post in posts" :key="post.id" class="col">
    <div class="card h-100">
      <img :src="post.image" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{post.title}}</h5>
        <p class="card-text">{{post.description}}</p>
      </div>
      <div class="card-footer">
        <small class="text-muted">Last updated {{post.timestamp}} ago</small>
      </div>
    </div>
  </div>
</div>
</div>

</template>
<script>
 import{getAPI} from "../axios-api"


export default {
  name:"Posts",
  data: () => ({
    posts: [],
    

  }),


    methods: {

    async getPost () {

      const postData = await getAPI.get('api/product-list/')


      this.posts.push(...postData.data);

      console.log(postData.data)

      
    },

   

  },
  created(){

    this.getPost();

   },



}
</script>
<style >

</style>