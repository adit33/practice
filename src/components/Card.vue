<template>
     <div class="card">
              <div class="card-content">
                <p class="title">
                  {{ product.description }}
                </p>
                <p class="subtitle">
                  Jeff Atwood
                </p>
              </div>
              <footer class="card-footer">
                <p class="card-footer-item">
                  <span>
                    {{ product.price }}
                  </span>
                </p>
              </footer>
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
    box-shadow: 9px 7px 40px -6px rgba(0,0,0,0.25);
    height:300px;
}
</style>


<script>

export default {
    name:'Card',
    props:['product']
}
</script>

