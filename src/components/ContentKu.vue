<template>
<div class="row">
  <div v-for="i in posts" class="col-sm-6 col-md-4">
    <div class="thumbnail">
      <img :src="i.urlToImage" alt="">
      <div class="caption">
        <h3>{{ i.title}}</h3>
        <p>{{i.description}}</p>
        <p><a @click="detail(i)" class="btn btn-primary" role="button" >Button</a> <a href="#" class="btn btn-default" role="button">Button</a></p>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios"
export default {
  name: "ContentKu",
  data() {
    return {
      //   halo: "Selamat datang"
      posts: []
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      axios
        .get(
          "https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=109cafd7e6a94b0cae047707712c8c25"
        )
        .then(response => {
          console.log(response);
          this.posts = response.data.articles;
        })
        .catch(err => {
          console.log(err);
        });
    },
    detail(data) {
        console.log('====================asasasas================');
        console.log(data);
        console.log('====================================');
        this.$store.commit('setFilm', data)
        this.$router.replace({ 'path': "/detail" });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
