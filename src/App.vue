<template>
  <div id="app">
    <input type="text" name="name" class="form-control" v-model="search">   
        <button @click="onSubmit(search)">Submit</button>
        {{search}}
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      response: null,
      search: ''
    };
  },
  methods: {
    onSubmit(query) {
      axios.get(' https://api.jikan.moe/v3/search/anime?q=naruto')
    .then(res =>{
      console.log(query)
      this.response = res.data.results
      console.log(this.response)
    })
    .catch(error => console.log(error))
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
