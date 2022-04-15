<template>
  <section class="productMarkets">
    <!-- <div class="container"> -->
      <h2>{{headerTitle}}</h2>

      <ul>
        <li
          v-for="(marketInfo, i) in markets"
          :key="i"
        >
          <figure aria-hidden="true">
            <img :src="require(`@/assets/img/${marketInfo.img}.png`)" />
          </figure> 

          <h3>
            <a :href="marketInfo.url">
              {{ marketInfo.label }}
            </a>
          </h3>
        </li>
      </ul>
    <!-- </div> -->
  </section>
</template>

<script>
export default {
  name: 'ProductMarkets',
  props: {
    headerTitle: String,
    markets: Array
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

section {
  margin: 0;
  padding: 1rem 1.5rem 0;
  background-color: #ddd;

  display: none;
}

h2 {
  margin: 0;
  padding: 0;
}

ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

li {
  display: flex;
  flex: 0 0 auto;
  flex-direction: column;
  margin: 0 auto 1rem;
  padding: 0;
  max-width: 109px;
  background-color: #fff;
  box-shadow: 0px 5px 8px -7px #000;
}

figure {
  flex: 1 0 auto;
  height: 76px;
  width: 109px;
  margin: 0;
}

h3 {
  flex: 1 1 auto;
  align-self: center;
  margin: 0;
  padding: 1rem 0.8rem;
  
  font-size: 0.9rem;
  line-height: 1.2;
  color: #333;

  display: grid;
  align-content: center;
  min-height: 66px;
}

a {
  color: #333;
  text-decoration: none;
}


@media screen and (min-width: 768px) {
    section {
      display: block;
    }
}

</style>
