<template>
  <div>
    <app-header></app-header>
    <router-view></router-view>
  </div>
</template>
<script>
  import addBlog from './components/addBlog.vue';
  import showBlogs from './components/showBlogs.vue';
  import header from './components/header.vue';
  import singleBlog from './components/singleBlog.vue';

  export default{
    components : {
      'add-blog': addBlog,
      'show-blogs': showBlogs,
      'app-header' : header,
      'single-Blog' : singleBlog
    },
    data(){
      return{

      }
    }
  }
</script>
<style>
body{
  marks: 0;
  font-family: 'Nunito SemiBold';
}
</style>