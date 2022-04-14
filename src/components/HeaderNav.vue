<template>
  <nav>
    <figure>
      <a href="#"><img src="@/assets/img/logo.png" /></a>
    </figure>

    <ul>
      <li><a href="#"><img src="@/assets/ic/white/ic_search.png" /></a></li>
      <li><a href="#"><img src="@/assets/ic/white/ic_shopping_cart.png" /></a></li>
      <li><a href="#"><img src="@/assets/ic/white/ic_person.png" /></a></li>
      <li><a href="#"><img src="@/assets/ic/white/ic_menu.png" /></a></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'HeaderNav',
  props: {
    msg: String
  }
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

</style>
