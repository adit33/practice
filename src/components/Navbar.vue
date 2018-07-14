<template>
<div>
  <nav class="navbar is-info">
  <div class="navbar-brand">
    <a class="navbar-item" href="https://bulma.io">
      <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: a modern CSS framework based on Flexbox" width="112" height="28">
    </a>
    <div class="navbar-burger burger" data-target="navbarExampleTransparentExample">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </div>

  <div id="navbarExampleTransparentExample" class="navbar-menu">
    <div class="navbar-start">
      <a class="navbar-item" href="https://bulma.io/">
        Home
      </a>
      <div class="navbar-item has-dropdown is-hoverable">
        <a class="navbar-link" href="/documentation/overview/start/">
          Docs
        </a>
        <div class="navbar-dropdown is-boxed">
          <a class="navbar-item" href="/documentation/overview/start/">
            Overview
          </a>
          <a class="navbar-item" href="https://bulma.io/documentation/modifiers/syntax/">
            Modifiers
          </a>
          <a class="navbar-item" href="https://bulma.io/documentation/columns/basics/">
            Columns
          </a>
          <a class="navbar-item" href="https://bulma.io/documentation/layout/container/">
            Layout
          </a>
          <a class="navbar-item" href="https://bulma.io/documentation/form/general/">
            Form
          </a>
          <hr class="navbar-divider">
          <a class="navbar-item" href="https://bulma.io/documentation/elements/box/">
            Elements
          </a>
          <a class="navbar-item is-active" href="https://bulma.io/documentation/components/breadcrumb/">
            Components
          </a>
        </div>
      </div>
    </div>

    <div class="navbar-end">
      <div class="navbar-item">
        <div class="field is-grouped">
          <p class="control has-icons-right">
            <input class="input" v-model="input_search" @keyup="showSearchResult" @blur="hideSearchResult" type="search" placeholder="Search">
              <span class="icon is-small is-right">
                <i class="fas fa-search"></i>
              </span>
          </p>
        </div>
      </div>
    </div>
  </div>
</nav>

<div class="search__container" v-if="is_visible">
  <ul class="card">  
    <li class="search-item" v-for="product in test">
      <div class="search-item__image" style="background-image: url(http://placehold.it/100x100);"></div>
      <div class="search-item__content">
        <p class="text--medium">
           <a v-html="highlightText(product.name, input_search)"></a>
          <span class="label label--red text--upcase">Warning</span>
        </p>
          <div v-html="highlightText(product.description,input_search)"></div>
        <p class="text--small text--muted">{{ product.price }}</p>
      </div>
    </li>
  </ul>
</div>

</div>
   
</template>
<style lang="scss" scoped>
// Stuff that will already be in ext - probably.



// Background strip at top

.strip-background {
  position: absolute;
  z-index: 0;
  top: 0;
  width: 100%;
  height: 215px;
  background-color: #6891DC;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: top center;
}

// Generic cards

.card {
  background: #FFFFFF;
  box-shadow: 0 2px 6px 0 rgba(0,0,0,0.20);
  border-radius: 8px;
  padding: 20px;
  @media screen and (min-width: 768px) {
    padding: 30px;
  }
}

// Search results

.search__container {
  padding:10px;
  width: 100%;
  margin: auto;
  z-index: 1;
  position: absolute;
  left: 0;
  right: 0;
  transition: 1s;

  @media screen and (min-width: 768px) {
    width: 95%;
    margin-top: 0;
  }
}
.search-item {
  border-bottom: 1px solid #D3DCE6;
  padding-bottom: 20px;
  margin-bottom: 20px;
  display: flex;
  flex-wrap: wrap;
  
  &:last-child {
    border-bottom: none;
    padding-bottom: 0;
    margin-bottom: 0;
  }
  
  @media screen and (min-width: 768px) {
    flex-wrap: no-wrap;
  }
}
.search-item__content {
  padding-top: 2px;
  order: 5;
  width: 100%;
  @media screen and (min-width: 600px) {
    width: auto; 
  }
}
.search-item__image {
  order: 1;
  width: 34px;
  height: 34px;
  background-color: red;
  border-radius: 8px;
  margin-right: 15px;
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
  margin-bottom: 10px;
  
  @media screen and (min-width: 600px) {
    width: 80px;
    height: 80px;
    margin-bottom: 0;
  }
}
.search-item__options {
  order: 2;
  margin-left: auto;
  @media screen and (min-width: 600px) {
    order: 10;
  }
}

// Labels

.label {
  display: inline-block;
  border-radius: 4px;
  font-size: 10px;
  padding: 5px;
  vertical-align: middle;
}
.label--red {
  background-color: #FF4747;
  color: #FFFFFF;
}

// Buttons - some of the reset-y type styles may be in ext already - like removing borders etc

.button {
  display: inline-block;
  text-transform: uppercase;
  border: 0;
  border-radius: 8px;
  background-color: red;
  font-size: 14px;
  padding: 22px;
}
.button--small {
  font-size: 10px;
  padding: 10px;
}
.button--block {
  display: block;
  width: 100%;
}
.button--primary {
  background-color: #72CB36;
  color: #FFFFFF;
}
.button--outline {
  border: 1px solid #D3DCE6;
  color: #A1A1A1;
  background-color: transparent;
}

// Text modifiers

.text--upcase {
  text-transform: uppercase; 
}
.text--small {
  font-size: 14px;
}
.text--muted {
  color: #8F8F8F; 
}
.text--medium {
  font-weight: 400;
}
.text--center {
  text-align: center;
}

// Form elements

.form {
  width: 100%;
}
.highlight {
  color: #0096D9;
}
input[type="text"],
input[type="date"]{
  border: 0;
  border-bottom: 1px solid #D3DCE6;
  display: block;
  width: 100%;
  height: 60px;
  margin-bottom: 10px;
  font-size: 17px;
  padding: 10px 0 0 0;
  transition: all 0.3s ease;
  appearance: none;
  &:focus {
    outline: 0;
    border-color: #72A3FF;
  }
}
.input__w-placeholder {
  position: relative;
}
label {
  position: absolute;
  transition: all 0.1s ease;
  z-index: 1;
  left: 0;
  top: 20px;
  color: #A1A1A1;
  .focus &, .static-label & {
    top: 0;
    font-size: 12px;
  }
}


input[type=search] {
	padding: 9px 10px 9px 32px;
  width: 55px;
  
  opacity: 0;
	
	-webkit-border-radius: 10em;
	-moz-border-radius: 10em;
	border-radius: 10em;
	
	-webkit-transition: all .5s;
	-moz-transition: all .5s;
	transition: all .5s;
}
input[type=search]:focus {
	width: 500px;
	background-color: #fff;
  border-color: #66CC75;
  opacity: 100;
	
	-webkit-box-shadow: 0 0 5px rgba(109,207,246,.5);
	-moz-box-shadow: 0 0 5px rgba(109,207,246,.5);
	box-shadow: 0 0 5px rgba(109,207,246,.5);
}
</style>

<script>
document.addEventListener('DOMContentLoaded', () => {

  // Get all "navbar-burger" elements
  const $navbarBurgers = Array.prototype.slice.call(document.querySelectorAll('.navbar-burger'), 0);

  // Check if there are any navbar burgers
  if ($navbarBurgers.length > 0) {

    // Add a click event on each of them
    $navbarBurgers.forEach( el => {
      el.addEventListener('click', () => {

        // Get the target from the "data-target" attribute
        const target = el.dataset.target;
        const $target = document.getElementById(target);

        // Toggle the "is-active" class on both the "navbar-burger" and the "navbar-menu"
        el.classList.toggle('is-active');
        $target.classList.toggle('is-active');

      });
    });
  }

});
import axios from 'axios';
export default {
    name:'Navbar',
    data(){
      return {
        is_visible:false,
        input_search:null,
        products:[],
      }
    },
    mounted(){
      axios.get('http://localhost:3000/products').then(response=>{
        this.products=response.data;
      })
    },
    methods:{
      showSearchResult(){
        this.is_visible = true
      },
      hideSearchResult(){
        this.is_visible = false;
      },
      getSearchProducts(){
        if(this.input_search !== null){
          axios.get('products')
          .then(response=>{
            
          })
          .catch(errors=>{

          })
        }
      },
      highlightText: function (words, query) {
          function pregQuote (str) {
            return (str.trim() + '').replace(/([\\\.\+\*\?\[\^\]\$\(\)\{\}\=\!\<\>\|\:])/g, "\\$1")
          }
          var iQuery = new RegExp(pregQuote(query), 'ig')
          return words.toString().replace(iQuery, function (matchedTxt, a, b) {
            return ('<span style=\'color:#0096D9\'>' + matchedTxt + '</span>')
          })
        },
    },
    computed:{
      test(){
        return this.products.filter(t=>{
          let tmp = t.name.toLowerCase().includes(this.input_search);
          return tmp;
        })
      }
    }
}
</script>

