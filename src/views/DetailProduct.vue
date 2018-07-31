<template>
    <div>
        <breadcrumb></breadcrumb>
        <div class="columns is-multiline is-mobile">
            <div class="column is-one-quarter">
                <code>is-one-quarter</code>
            </div>
            <div class="column is-one-quarter">
                 <div class="card">
            <div class="card-image">
                <figure class="image is-4by3">
                <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
                </figure>
            </div>
            <div class="card-content">
                <div class="media">
                <div class="media-left">
                    <figure class="image is-48x48">
                    <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
                    </figure>
                </div>
                <div class="media-content">
                    <p class="title is-4">{{ product.name }}</p>
                </div>
                </div>

                <div class="content">
                    {{ product.description }}
                <h4>{{ product.price }}</h4>
                <br>
                <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
                </div>
            </div>
            </div>
            </div>
        </div>
       
    </div>
</template>
<script>
import axios from 'axios';
import Breadcrumb from "./../components/Breadcrumb";
export default {
    name:'DetailProduct',
    components:{
        'breadcrumb':Breadcrumb
    },
    data(){
        return {
            product:null,
        }
    },
    mounted(){
        this.getProduct();
    },
    methods:{
        getProduct(){
            let url = 'http://localhost:3000/products/'+this.$route.params.id;
            axios.get(url).then(response=>{
                this.product=response.data;
            });
        }
    }
}
</script>
