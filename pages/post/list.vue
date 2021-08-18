<template>
    <div class="text-center" >  
    <b-card 
    title= "Post Title"  
    img-src="https://picsum.photos/600/300/?image=25"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="text-center mt-3 mb-2"
  >
    <h1>Post List</h1>
<h2 v-for="post in posts" :key="post.id">{{ post.title}}</h2>
 <div class="card-header mt-3"></div> 

 </b-card>
 </div>

</template>
<script>
import {mapState} from 'vuex'
export default {
    name: 'PostList',
 async fetch({store, $axios, error}){
  try{
 const {data} = await $axios.get('/posts');
 store.dispatch('setPosts', data);
  }catch(err){
    error({statusCode: 500, message: 'Oops, something went wrong'})
  }
},
   computed: {
  ...mapState({
    posts: state => state.post.posts
  })
    },

    
}
</script>