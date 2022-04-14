<template>
  <div class="autocomplete">
    <input
        v-model="searchTerm"
        @input="onChange"
        @keydown.down="onArrowDown"
        @keydown.up="onArrowUp"
        @keydown.enter="onEnter"
        type="text"
        placeholder="What are you looking for?"
    />
    <ul
        v-show="isOpen"
        class="autocomplete-results"
    >
      <li
        v-for="(result, i) in results"
        :key="i"
        @click="setResult(result)"
        class="autocomplete-result"
        :class="{ 'is-active': i === arrowCounter }"
      >
        {{ result }}
      </li>
    </ul>
  </div>
</template>


<script>
export default {
  name: 'SearchAutocomplete',
  props: {
    items: {
      type: Array,
      required: false,
      default: () => [],
    },
  },
  data() {
    return {
      searchTerm: '',
      results: [],
      isOpen: false,
      arrowCounter: -1,
    };
  },
  mounted() {
    document.addEventListener('click', this.handleClickOutside);
  },
  // Example said to use destroyed, which is deprecated
  unmounted() {
    document.removeEventListener('click', this.handleClickOutside);
  },  
  methods: {
    filterResults() {
        this.results = this.items.filter(item => item.toLowerCase().indexOf(this.searchTerm.toLowerCase()) > -1);
    },
    onChange() {
        console.log("onChange: searchTerm = ", this.searchTerm);
        this.filterResults();
        // this.isOpen = true;
        this.isOpen = (this.searchTerm !== '' && this.results.length);
    },
    setResult(result) {
        // console.log("setResult");
        this.searchTerm = result;
        this.isOpen = false;
        this.arrowCounter = -1;
    },
    handleClickOutside(event) {
        if (!this.$el.contains(event.target)) {
            this.isOpen = false;
        }
    },
    onArrowDown() {
        if (this.arrowCounter < this.results.length) {
            this.arrowCounter = this.arrowCounter + 1;
        }
    },
    onArrowUp() {
        if (this.arrowCounter > 0) {
            this.arrowCounter = this.arrowCounter - 1;
        }
    },
    onEnter() {
        this.searchTerm = this.results[this.arrowCounter];
        this.arrowCounter = -1;
        this.isOpen = false;
    },    
  }
};
</script>

<style>

    .autocomplete {
        position: relative;
        width: 100%;
        margin: 0 auto;
        padding: 0;
    }

    input[type="text"] {
        background-color: #fff; 
        padding: 0.8rem;
        width: 100%;
        border: none;
        border-radius: 0.2rem;
        padding-right: 3rem;
    }

    ::placeholder {
        color: #999;
    }

  .autocomplete-results {
    padding: 0;
    margin: 0;
    border: 1px solid #eeeeee;
    height: 120px;
    min-height: 1em;
    max-height: 7.2em;    
    overflow: auto;
    background-color: #fff;
    position: absolute;
    /* Ideally, these would be directly tied to the padding and spacing of the input, probably with variables */
    top: 2.6rem;
    left: 0.2rem;
    right: 0.2rem;
  }

  .autocomplete-result {
    list-style: none;
    text-align: left;
    padding: 0.5rem 0.6rem;
    cursor: pointer;
  }

  .autocomplete-result.is-active,
  .autocomplete-result:hover {
    background-color: #4c873c;
    color: white;
  }
</style>
