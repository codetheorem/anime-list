<template>
  <div id="app">
    <div class="outer">
      <div class="middle">
        <div class="inner">
          
          <img src="https://wallpaperaccess.com/full/39052.png" class="img-fluid" alt="Responsive image">
          <br><br>
          <input type="text" name="name" class="form-control" v-model="search" @input="onSubmit(search)" placeholder="Search anime...">   
      
        </div>
          <div id="result">
                  <ul class="list-group list-group-flush">
                    <li v-for="(item,i) in response" :key="i" v-show="i<=10" class="list-group-item" @click="addtowatchlist(item)" >{{item.title}}</li>
                  </ul>
        </div>
          <appcard  v-for="(item,i) in watchlist" :key="i"
                  :title="item.title"
                  :score="item.score"
                  :episodes="item.episodes"
                  :synopsis="item.synopsis"
                  :image="item.image_url"
                  class="col-lg-3 col-md-3 col-sm-6"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import cardVue from './components/card.vue';

export default {
  name: 'App',
  components: {
    appcard: cardVue
  },
  data() {
    return {
      response: null,
      search: '',
      watchlist:[],
    };
  },
  methods: {
    onSubmit(query) {
      axios.get(' https://api.jikan.moe/v3/search/anime?q='+query)
    .then(res =>{
      console.log(query)
      this.response = res.data.results
      console.log(this.response)
    })
    .catch(error => console.log(error))
    },
    addtowatchlist(item){
       this.watchlist.push(item);
    }
  }
}
</script>

<style>
.outer {
  display: table;
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}

.middle {
  display: table-cell;
  vertical-align: middle;
}

.inner {
  margin-left: auto;
  margin-right: auto;
  width: 400px;
  padding: 10px;
  /*whatever width you want*/
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
ul{
  list-style: none;
  width: 50%;
  margin: auto;
}
.wrapper ul {
  display: inline-block;
  margin: 0;
  padding: 0;
  zoom:1;
  *display: inline;
}
.wrapper li {
  padding: 2px 5px;
}
img{
  border-radius: 15px;
  border: 2px solid greenyellow;
}

li:hover{
cursor: pointer;
}
</style>
