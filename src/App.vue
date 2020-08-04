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
      search: 'wdw'
    };
  },
  methods: {
    onSubmit(query) {
      axios.get(' https://api.jikan.moe/v3/search/anime?q='+query)
    .then(res =>{
      console.log(res)
      this.response = res
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
