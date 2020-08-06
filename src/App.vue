<template>
  <div id="app">
    <div class="outer">
      <div class="middle">
        <div class="inner">
          <img src="https://wallpaperaccess.com/full/39052.png" class="img-fluid" alt="Responsive image">
          <br><br>
          <input type="text" name="name" class="form-control" v-model="search" @input="onsearch(search)" placeholder="Search anime...">   
        </div>
        
    <div id="result" v-show="searchdisplay">
       <ul class="list-group list-group-flush">
        <li v-for="(item,i) in response" :key="i" @click="addtowatchlist(item)" class="list-group-item">
          {{item.title}}
        </li>
       </ul>
    </div>

      <br><br>

      <div v-if="display" id="result">
        <h1>Watch List</h1>
       <ul>
        <div class="row">
         <appcard  v-for="(item,i) in watchlist" :key="i"
                  :data="item"
                  :index="i"
                  @removed="remove($event)"
                  @watch="watch($event)"/>
        </div>
       </ul>
      </div>

      <br><br>


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
    appcard: cardVue,
  },
  data() {
    return {
      response: null,
      search: '',
      watchlist: [],
      display: false,
      searchdisplay: true,
    };
  },
  methods: {
    onsearch(query) {
      axios.get(' https://api.jikan.moe/v3/search/anime?q='+query)
    .then(res =>{
      this.response = res.data.results
      this.response= this.response.slice(0,10)
    })
    .catch(error => console.log(error))
    this.searchdisplay=true
    },
    addtowatchlist(item) {
      this.display = true
      this.searchdisplay=false
      item.airing=false
      this.watchlist.push(item)
      const parsed = JSON.stringify(this.watchlist);
      localStorage.setItem('watchlist', parsed);
    },
    remove(index) {
      this.watchlist.splice(index,1);
      if(this.watchlist.length<1){
        this.display=false
      }
      const parsed = JSON.stringify(this.watchlist);
      localStorage.setItem('watchlist', parsed);
    },
    watch(index) {
      if(this.watchlist[index].airing){
        this.watchlist[index].airing = true
      }else{
        this.watchlist[index].airing =false
      }
      const parsed = JSON.stringify(this.watchlist);
      localStorage.setItem('watchlist', parsed);
    }
  },
  mounted() {
    if (localStorage.getItem('watchlist')) {
      try {
        this.watchlist = JSON.parse(localStorage.getItem('watchlist'));
        console.log(this.watchlist)
        if(this.watchlist.length>0){
          this.display=true
        }
      } catch(e) {
        localStorage.removeItem('watchlist');
      }
    }
  },
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
h1{
  text-align: center;
}
</style>
