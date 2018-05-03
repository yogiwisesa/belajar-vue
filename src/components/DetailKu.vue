<template>
    <div>
        <h1>{{ film.title }}</h1>
        <button @click="back">Kontol</button>

    </div>
</template>

<script>
export default {
  name: "DetailKu",
  data() {
    return {
      halo: "Selamat datang"
    };
  },
  computed: {
    film(){
      return this.$store.state.film
    }
  },
  methods: {
    back (){
       this.$router.replace({path:'/'})
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
