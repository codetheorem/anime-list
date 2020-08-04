<template>
    <div class="-shadow" id="box">
      <h4 class="title">
        title: {{ title }}
      </h4>
      <span class="eyebrow">
        score: {{ score }}/10
      </span>
      <br>
      <span class="eyebrow">
        Episodes: {{ episodes }}
      </span>
      <br>
        <span class="eyebrow">
        synopsis: {{ synopsis }}
      </span>
      <br>
    </div>
</template>

<script>
export default {
    props: ['title','episodes','score','synopsis'],
    
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