<template>
  <p>Sinle Page of the site</p>
  {{blog}}
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      blog: null,
    };
  },
  mounted() {
    axios
      .get(`http://localhost:3000/posts`+ this.$route.params.id)
      .then((res) => {
          this.blog=res.data
      
      });
  },
};
</script>

<style></style>
