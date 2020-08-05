<template>
<div class="card">
  <div class="row">
    <div class="col-4">
        <img :src="data.image_url" class="img-thumbnail" alt="...">
    </div>
    <div class="col-8">
      <div class="card-body">
        <h1 class="card-title">{{data.title}}</h1>
        <div class="row" id="info">
          <div class="col-sm">
            Episodes: {{data.episodes}}
          </div>
          <div class="col-sm">
            Score: {{data.score}}/10
          </div>
          <div class="col-sm">
            Rating: {{data.rated}}
          </div>
        </div>
        <br>
        <p class="card-text">{{data.synopsis}}</p>
        <button type="button" class="btn btn-success">Watched</button>
        <button type="button" class="btn btn-danger">Remove</button>
        <a :href="data.url" target="_blank"><button  type="button" class="btn btn-primary">See more...</button></a>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
    props: ['data'],
    
}
</script>

<style scoped>
#info{
  font-size: 1.5rem;
  box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.2), 0 1px 5px 0 rgba(0, 0, 0, 0.19);
}
.card {
  padding: 10px;
  margin-bottom: 24px;
  margin: 5px;
  width: 100%;
  transition: all 0.2s linear;
  cursor: pointer;
  text-align: center;
  border-top: 4px solid lightgreen;
  box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.2), 0 1px 5px 0 rgba(0, 0, 0, 0.19);
}
.card:hover {
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
img{
  border-radius: 15px;
  margin-top: 10px;
  margin-left: auto;
  margin-right: auto;
  display: block;
}
button{
  margin: 10px;
}
</style>