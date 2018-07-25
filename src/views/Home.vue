<template>
<div>
  <section class="section">
      <breadcrumb></breadcrumb>
       <div class="tile is-ancestor">
        <div class="tile is-3 is-vertical is-parent">
          <div class="tile is-child box">
            <article class="notification is-danger">
              <p class="title">Wide tile</p>
              <p class="subtitle">Aligned with the right tile</p>
              <div class="content">
                <!-- Content -->
              </div>
            </article>
          </div>
          <div class="tile is-child box">
            <article class="notification is-warning">
              <p class="title">Wide tile</p>
              <p class="subtitle">Aligned with the right tile</p>
              <div class="content">
                <!-- Content -->
              </div>
            </article>
          </div>
        </div>
      <div class="tile is-parent">
      <div class="tile is-child box">
        <div class="columns is-multiline">
          <div class="column is-6-tablet is-4-desktop" v-for="product in products">
           <card :product="product"></card>
          </div>
        </div>
      </div>
    </div>
    </div>
    </section>
    <footer class="footer">
  <div class="content has-text-centered">
    <p>
      <strong>Bulma</strong> by <a href="https://jgthms.com">Jeremy Thomas</a>. The source code is licensed
      <a href="http://opensource.org/licenses/mit-license.php">MIT</a>. The website content
      is licensed <a href="http://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY NC SA 4.0</a>.
    </p>
  </div>
</footer>
</div>
</template>



<style>
#app {
  margin-bottom: 60px;
  background-color: #F5F5F5;
  font-family: -apple-system, BlinkMacSystemFont, 
    "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", 
    "Fira Sans", "Droid Sans", "Helvetica Neue", 
    sans-serif;
  * {
    box-sizing: border-box;
  }
}
p {
  margin: 5px 0;
  font-weight: 300;
}

</style>

<script>
import Breadcrumb from "./../components/Breadcrumb";
import Card from "./../components/Card";
import axios from 'axios';
export default {
  components:{
    'breadcrumb':Breadcrumb,
    'card':Card
  },
  data(){
    return {
      products:[]
    }
  },
  mounted(){
    axios.get('http://localhost:3000/products').then(response=>{
      this.products=response.data;
    })
  }
}
</script>

