<template>
  <nav>
    <figure>
      <a href="/"><img src="@/assets/img/logo.png" alt="Platt" /></a>
    </figure>

    <ul>
      <li><a @click.stop.prevent="clickSearch"><img src="@/assets/ic/white/ic_search.png" /></a></li>
      <li><a @click.stop.prevent="clickCart"><img src="@/assets/ic/white/ic_shopping_cart.png" /></a></li>
      <li><a @click.stop.prevent="clickUser" class="loggedIn"><img src="@/assets/ic/white/ic_person.png" /></a></li>
      <li><a @click.stop.prevent="clickMenu"><img src="@/assets/ic/white/ic_menu.png" /></a></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'HeaderNav',
  // props: {
  //   msg: String
  // },
  methods: {
    clickSearch(event) {
        if (event) {
          event.preventDefault()
        }
        console.log('Do (advanced?) search stuff');
        // return false;
    },
    clickCart(event) {
        if (event) {
          event.preventDefault()
        }

        console.log('Do shopping cart stuff');

        // return false;
    },
    clickUser(event) {
        if (event) {
          event.preventDefault()
        }

        console.log('Do login stuff, probably');

        // return false;
    },
    clickMenu(event) {
        if (event) {
          event.preventDefault()
        }

        console.log('Do menu stuff (show/hide)');

        // return false;
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

nav {
  margin: 0 auto;
  padding: 0 0 0.6rem;
  width: 100%;
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
}

figure {
  display: inline-flex;
  flex: 1 1 auto;
  padding: 0;
  margin: 0;
}

ul {
  display: flex;
  display: inline-flex;
  flex: 1 1 auto;

  list-style-type: none;
  padding: 0;
  margin: 0;
  justify-content: flex-end;
}
ul li {
  display: inline-flex;
  flex: 0 0 auto;
  padding: 0;
  margin: 0;
  width: 2.5rem;
  justify-content: flex-end;
}

ul li img {
  display: inline-block;
}

.loggedIn {
  position: relative;
}

.loggedIn:after {
  content: '';
  height: 6px;
  width: 6px;
  line-height: 6px;
  border-radius: 50%;
  background-color: #eebd31;
  color: #eebd31;
  text-align: center;
  position: absolute;
  top: -5px;
  right: -6px;
  /* I see a drop shadow in the comp, I'm not to to tweak it beyond this. */
  box-shadow: inset -1px 3px 8px 5px #eebd31, 2px 5px 16px 0px #666, 5px 5px 15px 5px rgba(0,0,0,0);
  box-shadow: 0px 10px 13px -7px #000000, 5px 5px 15px 5px rgba(0,0,0,0);
} 

</style>
