<template>
    <header>
      <div class="container header-nav">
        <HeaderNav />
      </div>
      <div class="container">
        <SearchAutocomplete
          :items="this.info"
        />
      </div>
    </header>
    <QuickLinks :links="[
      {label: 'Shop all categories', url: '/categories', icon: 'categories'},
      {label: 'My Catalog', url: '/mycatalog', icon: 'mycatalog'},
      {label: 'My List', url: '/mylist', icon: 'mylist'},
      {label: 'Live Help', url: '/livehelp', icon: 'livehelp'},
      {label: 'PIM', url: '/pim', icon: 'pim'},
      {label: 'Account', url: '/account', icon: 'account'},
      {label: 'Branch Locations', url: '/branches', icon: 'branches'},
    ]"/>
</template>

<script>
import axios from 'axios'

// import HelloWorld from './components/HelloWorld.vue'
import HeaderNav from './components/HeaderNav.vue';
import QuickLinks from './components/QuickLinks.vue';
import SearchAutocomplete from './components/SearchAutocomplete.vue';

export default {
  name: 'App',
  data () {
    return {
      info: null
    }
  },
  components: {
    SearchAutocomplete,
    HeaderNav,
    QuickLinks,
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

* {
  box-sizing: border-box;
}

html, body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #262626;
}

header {
  background-color: #4c873c;
  margin: 0;
  padding: 1rem 0;
}

.container {
  width: 100%;
  margin: 0;
  /* padding: 0px; */
  padding: 0 1.5rem;
}

@media screen and (min-width: 768px) {
    .container.header-nav {
        padding: 0 0.5rem;
    }
}

</style>
