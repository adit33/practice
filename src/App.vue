<template>
  <div id="app">
    <navbar></navbar>
    
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

<style lang="scss">
$footer-background-color:#000000;
</style>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

<script>
import './assets/sass/app.scss';
import Breadcrumb from "./components/Breadcrumb";
import Navbar from "./components/Navbar";
import Card from "./components/Card";
import axios from 'axios';
export default {
  components:{
    'navbar':Navbar,
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

