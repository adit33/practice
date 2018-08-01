<template>
  <div id="app">
 
    <navbar></navbar>
    
    <router-view :key="$route.fullPath"></router-view>

    
  </div>
</template>


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

