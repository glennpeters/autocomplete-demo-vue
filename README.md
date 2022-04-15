# Vue AutoComplete Example

Building towards the guidelines below, limiting the scope because of external time pressures.

This is a demonstration of principles, not an attempt to manage pixel-perfect design.

Using an <a href="https://www.digitalocean.com/community/tutorials/vuejs-vue-autocomplete-component#step-1-setting-up-the-project">Autocomplete tutorial for time management</a>.

I had implemented autocomplete from scratch previously, but it's general good practice to use existing code to speed things up.

Customized to hide the autocomplete on an empty search field, as well as hiding with empty (post-filtered) results.

Added fetch to SWAPI with axios. Note: It's just doing an initial fetch.  There's a lot of fine tuning that could be done going into the weeds with timing of requests and requesting the specific search term incrementally, but that's outside the scope of this.

Things that could be done for scalability or usability, skipping for time:
* General pixel-perfect rabbit holes
* Moving Header items to general Header component
* Make Search icon in the search bar a positioned submit button

Short term TODO:
- [x] Don't display autofill on blank input
- [X] https://www.npmjs.com/package/vue-axios
- [ ] Search bar search icon
- [ ] Mobile only quick links arrows

Some Issues:
* Renamed "ic_chat - active.png" to "ic_chat_active.png"
* Icons change between mobile and desktop for Live Help -- Noted that the green icon is labelled "Active", created an .active class style to differentiate (Also, the black and green icons are flipped)
* Black Account icon missing.  Inverted white "person" icon




## Code Challenge Requirements

In the code challenge, you will take PDF mockups and recreate them in web format, including all assets in the attached file. 

We are looking for a responsive site (tablet and mobile views) with some simple JavaScript, good structure, and solid CSS layout. We would like to see custom media queries. You can use a JavaScript framework (e.g. Vue, Angular 2, React, etc.).

### Key points to this challenge are:

- [ ] Make an ‘autocomplete’ of sorts in the main search bar using any api: 
    * https://swapi.co/api/ 
    * https://swapi.co/documentation
    * https://dog.ceo/dog-api/
    * etc.
- [X] You can do it in any JavaScript framework.
- [X] Do not use a CSS framework (Bootstrap, Bulma, Foundation, etc.)(Normalize.css is okay to use).
- [ ] Make sure the application can be installed and built (npm etc).
- [X] We are looking for structure and how you would build something as if you were planning for a scalable application. 
- [ ] We would like to see custom media queries.

### Implementation Specifics
- [ ] Write up documentation
- [X] Static autocomplete starter
- [X] Dynamic autocomplete -- initial data fetch for data 


## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
