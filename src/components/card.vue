<template>  
  <li class="card mt-2" style="width: 18rem;">
    <img :src="image" class="card-img-top" alt="anime-image">
    <div class="card-body">
      <h5 class="card-title">{{title}}</h5>
      <p class="card-text">{{synopsis}}</p>
      <a :href="url" target="_blank" class="btn btn-primary">see details</a>
    </div>
  </li>
</template>

<script>
export default {
    props: ['title','episodes','score','synopsis','image', 'url'],
    
}
</script>

<style scoped>
#box {
  padding: 20px;
  margin-bottom: 24px;
  transition: all 0.2s linear;
  cursor: pointer;
  border-top: 4px solid lightgreen;
  box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.2), 0 1px 5px 0 rgba(0, 0, 0, 0.19);
}
#box:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2), 0 1px 15px 0 rgba(0, 0, 0, 0.19);
}
.title {
  margin: 0;
  color: black;
}
a {
  text-decoration: none;
}
#switch{
    display: block;
    margin: 0 auto;
}
h4{
    text-align: center;
}
#time{
    float: right;
}
h6{
    text-align: center;
}
</style>