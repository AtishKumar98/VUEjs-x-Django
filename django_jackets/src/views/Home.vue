<template>
    <div class="home">
    <section class="hero is-medium is-dark mb-6">
        <div class="hero-body has-text-centered">
            <p class="title mb-6">
                Welcome to Djacket
            </p>
            <p class="subtitle">
                The best jacket store online
            </p>
        </div>
    </section>
     <div class="columns is-multiline m-2">
      <div class="column is-12">
          <h2 class="is-size-2 has-text-centered">Latest products</h2>
      </div>
      <div class="coloumn is-3 m-2"
        v-for="product in latestProducts"
        v-bind:key="product.id"
        >
        <div class ="box">
          <figure class="image mb-4 m-2">
            <img :src="product.get_thumbnail">
          </figure>
          <h3> {{product.name}}</h3>
          <h4> ${{product.price}}</h4>
          VALUE DETAILS
        </div>
    </div>
     </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'Home',
  data() {
    return {
      latestProducts:[]

    } 
  },
  components: {  
  },
  mounted() {
    this.getLatestProducts()

  },
  methods:{
    getLatestProducts(){
      axios.get('api/v1/latest-products/').then(respose =>{
        this.latestProducts = respose.data
      })
      .catch(error=>{
        console.log(error)
      })
    }
  }


}
</script>
