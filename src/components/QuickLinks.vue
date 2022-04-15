<template>
  <section aria-label="Quick Links">
    <ul>
      <li
        v-for="(linkInfo, i) in links"
        :key="i"
      >
        <a 
            :href="linkInfo.url"
            :class="linkInfo.icon"
        >
            {{ linkInfo.label }}
        </a>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'QuickLinks',
  props: {
    links: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

ul {
    list-style-type: none;
    padding: 0;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    /* background-color: #999; */
    padding: 1px 0 0;
    width: 94%;

    font-size: 1rem;
}
li {
    display: inline-block;
    display: flex;
    flex: 0 0 33.2%;
    /* margin-bottom: 1px;     */
    /* using background as border */
    padding: 0.6em 1.5rem;

    /* Mobile only quick links arrows */
    background-image: url('~@/assets/ic/black/ic_arrow_forward.png');
    background-repeat: no-repeat;
    background-position: calc(100% - 20px) center;
    background-color: #fff;
    border-bottom: 1px solid #999;
    width: 100%;
}

li:first-of-type {
    font-size: 1.1rem;
    font-weight: 800;
    padding: 1.4rem 1.5rem;
}

li:last-of-type {
    margin-bottom: 0;
}

a {
    color: #333;
    text-decoration: none;
    display: inline-block;
    text-align: left;
    width: 100%;
    padding-left: 30px;

    /* Mobile only quick links arrows */
    /* Setting a default because no icon among icons would be weirder than a duplicate */
    background-image: url('~@/assets/ic/black/ic_categories.png');
    background-repeat: no-repeat;
    background-position: left center;
}

/* Shop all categories */
.categories {
    background-image: url('~@/assets/ic/black/ic_categories.png');
}

/* My Catalog */
.mycatalog {
    background-image: url('~@/assets/ic/black/ic_playlist_add_check.png');
}

/* My List */
.mylist {
    background-image: url('~@/assets/ic/black/ic_list.png');
}

/* Live Help */
.livehelp {
    background-image: url('~@/assets/ic/black/ic_comment.png');
}

/* Live Help ACTIVE */
.livehelp.active {
    background-image: url('~@/assets/ic/green/ic_chat_active.png');
}

/* PIM */
.pim {
    background-image: url('~@/assets/ic/black/ic_check_circle.png');
}

/* Account */
.account {
    background-image: url('~@/assets/ic/black/ic_account.png');
}

/* Branch locations */
.branches {
    background-image: url('~@/assets/ic/black/ic_place.png');
}

@media screen and (min-width: 768px) {
    ul {
        flex-direction: row;
        flex-wrap: wrap;
        gap: 1px;
        text-align: center;
        width: 100%;
        background-color: #999;
    }

    li {
        background-image: none;
        flex: 0 0 33.2%;
        justify-content: center;
        border: none;
    }

    li:first-of-type {
        flex: 0 0 100%;
    }

    a {
        text-align: center;
        width: auto;
        display: inline-block;
    }
}

</style>
