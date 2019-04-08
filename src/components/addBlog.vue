<template>
  <div id="add-blog">
    <h2>Add New Blog Post</h2>
    <form v-if="!submitted">
      <label>Blog Title : </label>
      <input type="text" v-model.lazy="blog.title" required/>
      <label>Blog Content : </label>
      <textarea v-model.lazy="blog.content"></textarea>
      <div id="checkboxes">
        <label>Batsman</label>
        <input type="checkbox" value="Batsman" v-model="blog.categories"/>

        <label>Bowler</label>
        <input type="checkbox" value="Bowler" v-model="blog.categories"/>

        <label>Allrounder</label>
        <input type="checkbox" value="Allrounder" v-model="blog.categories"/>

        <label>WicketKeeper</label>
        <input type="checkbox" value="WicketKeeper" v-model="blog.categories"/>

        <label>Captain</label>
        <input type="checkbox" value="Captain" v-model="blog.categories"/>
      </div>
      <label>Author : </label>
      <select v-model="blog.author">
        <option v-for="author in authors">{{author}}</option>
      </select>
      <button v-on:click.prevent="post">Add Blog</button>
    </form>
    <div v-if="submitted">
      <h3>Thanks for adding your Blog</h3>
    </div>
    <div id="preview">
      <h3>Preview Blog</h3>
      <p>Blog Title : {{blog.title}}</p>
      <p>Blog Content</p>
      <p>{{blog.content}}</p>
      <p>Blog Categories : </p>
      <ul>
        <li v-for="category in blog.categories">{{category}}</li>
      </ul>
      <p>Author : {{blog.author}}</p>
    </div>
  </div>
</template>
<script>
  export default{
    data(){
      return{
        blog : {
          title : "",
          content : "",
          categories : [],
          author : ""
        },
        authors : ["Deepanshu", "Risabh", "Chinmay", "Bhuvnesh"],
        submitted : false
      }
    },
    methods : {
      post : function() {
        this.$http.post('https://basic-blog-123ab.firebaseio.com/posts.json', this.blog).then(function(data){
          console.log(data);
          this.submitted=true;
        });
      }
    }
  }
</script>
<style>
#add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
  display : inline-block;
  margin-right : 10px;
}
#checkboxes label{
  display : inline-block;
}
</style>