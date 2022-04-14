<template>
  <div class="autocomplete">
    <input
        v-model="searchTerm"
        @input="onChange"
        @keydown.down="onArrowDown"
        @keydown.up="onArrowUp"
        @keydown.enter="onEnter"
        type="text"
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
        this.isOpen = (this.searchTerm !== '');
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
  }

  .autocomplete-results {
    padding: 0;
    margin: 0;
    border: 1px solid #eeeeee;
    height: 120px;
    min-height: 1em;
    max-height: 6em;    
    overflow: auto;
  }

  .autocomplete-result {
    list-style: none;
    text-align: left;
    padding: 4px 2px;
    cursor: pointer;
  }

  .autocomplete-result.is-active,
  .autocomplete-result:hover {
    background-color: #4AAE9B;
    color: white;
  }
</style>
