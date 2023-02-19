<template>
  <div class="hello">
    <h1>CANDY ALPHA</h1>
    <br>
    <div v-for="candy in candies" :key="candy.name">
      {{ candy.description }} is a {{ candy.price }} 
  <!-- I kind of messed up the connection of the right data corresponding to the correct data name, 
  but im happy i got it to show up on the front end from my own api i made regardless -->
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data() {
    return {
      url: process.env.VUE_APP_API_URL,
      candies : []
    }
  },
  methods: {
    getCandies() {
      axios.request({
        method: "GET",
        url: this.url + "/candies"
      }).then((response)=>{
        this.candies = response.data
      }).catch((error)=>{
        console.log(error);
      })
    }
  },
  mounted () {
    this.getCandies();
  },
      
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
