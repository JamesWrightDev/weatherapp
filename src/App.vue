<template>
  <div class="div">
  <h1>Weather App</h1>
    <form action="">
      <input placeholder='Postcode' type="text">
      <button @click="fetch()" type='button'>Submit</button>
      <li>{{this.posts}}</li>
    </form>

  </div>


</template>

<script>
import axios from 'axios';
//OPEN Weather KEY ce8eda79a399891855e2791f7a095cc5

//


// RON https://ron-swanson-quotes.herokuapp.com/v2/quotes

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      posts:[],
    }
  },
  methods:{
      fetch(){
          axios.get('http://datapoint.metoffice.gov.uk/public/data/val/wxfcs/all/xml/3840?res=3hourly&key=3267e165-de61-46e5-a6ef-157f7cd0caa8')
          .then(response =>{
            console.log(response);
            this.posts = response.data
          })
          .catch(e => {
            console.log(e)
          })
          
      }

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
