<template>
  <div id="app">
    <SearchAutocomplete
      :items="this.info"
    />
  </div>
</template>

<script>
import axios from 'axios'

// import HelloWorld from './components/HelloWorld.vue'
// import Home from './components/Home.vue';
import SearchAutocomplete from './components/SearchAutocomplete.vue';

export default {
  name: 'App',
  data () {
    return {
      info: null
    }
  },
  components: {
    SearchAutocomplete
  },
  mounted () {
    axios
      .get('https://swapi.dev/api/people/')
      // .then(response => (this.info = response))
      .then((response) => {
        if (response.status === 200) {
          console.log("Success!  raw response.data = ", response.data);

          // All sorts of error checking can be done here depending on level of trust 
          this.info = (response.data.results).map(x => x.name);

          // Note also this is returning just the first slice of names
        }

        console.log("Success!  this.info = ", this.info);
      });
  },  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
