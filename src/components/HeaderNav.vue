<template>
  <nav>
    <figure>
      <!-- <img src="" /> -->
      Platt
    </figure>
    <ul>
      <li>S</li>
      <li>C</li>
      <li>P</li>
      <li>M</li>
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
  margin: 0;
  padding: 0;
  width: 100%;
}

figure {
  display: inline-flex;
  flex: 1 1 auto;
}

ul {
  display: flex;
  display: inline-flex;
  flex: 1 1 auto;

  list-style-type: none;
  padding: 0;
}
li {
  display: inline-flex;
  flex: 1 1 auto;
  margin: 0 10px;
}

</style>
