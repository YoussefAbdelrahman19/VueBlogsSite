<template>
  <div id="">
    <app-header></app-header>
    <div class="row">
    <router-link to='/' class="col">Home</router-link>
    <router-link to='/about' class="col">About</router-link>
    <router-link to='/master' class="col">Master</router-link>
    </div>

    <div>Tester</div>
    <div v-if="blogs">
      <blog-card v-for="blog in blogs" :key="blog.id" :data="blog"></blog-card>
      <div class="row">
        <div class="col-sm-4"></div>
      <button type="button" class="btn btn-primary text-center col-sm-2  m-3" @click="showmore()">Load More</button>
      </div>
    </div>
    <router-view></router-view>

  </div>
</template>

<style lang="scss"></style>
<script>
import AppHeader from "./components/app-header";
import BlogCard from "./components/blog-card";
import axios from "axios";
export default {
  name: "app",
  components: { AppHeader, BlogCard },
  data() {
    return {
      blogs: null,
      page:1,
    };
  },
  mounted(){
    // this.getBlogs(this.page);
   
  },
  methods:{
    getBlogs(page){
       axios.get(`http://localhost:3000/posts?_page=${page}&_limit=2`).then((response) => {
      console.log(response.data);
      console.log("Data ended");
      this.blogs =this.blogs?this.blogs.concat(response.data):response.data;

    });
    },
    showmore(){
      this.page++;
      this.getBlogs(this.page);
    }
  }
};
</script>
