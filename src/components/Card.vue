<template>
    <div class="card">
  <div class="card-image">
    <figure class="image is-4by3">
      <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
    </figure>
  </div>
  <div class="card-content">
    <div class="media">
      <div class="media-content">
        <p class="title is-4">{{product.name}}</p>
        <p class="subtitle is-6">{{ product.price }}</p>
      </div>
    </div>

    <div class="content">
      {{ product.description }}
      <a href="#">#css</a> <a href="#">#responsive</a>
      <br>
      <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
      <center>
        <router-link :to="{ path:'/product/'+product.id }" class="button is-info is-outlined">Buy</router-link>
      </center>
    </div>
  </div>
</div>
</template>

<style lang="css" scoped>
/* .card-footer{
    background-color: black;
      transform: translateY(0);
    height: 100px;
    transition: transform 0.3s;
}
.card-footer:hover{
    background-color: aqua;
    transform: translateY(calc(70px + 1em));
    
} */
.card{
    width: 100%;
    margin: 0px;
    box-shadow: 9px 7px 40px -6px rgba(0,0,0,0.25);
    transition: .3s;
    /* height:300px; */
}
.card:hover{
  width: 100%;
  transform: scale(1.1,1.1);
}
</style>


<script>

export default {
    name:'Card',
    props:['product']
}
</script>

