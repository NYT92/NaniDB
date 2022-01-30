<template>
  <main class="search-container">
    <app-navbar></app-navbar>
    <div class="search-hero">
      <div class="search-container1">
        <h1 class="search-text">Search Any Anime and Characters</h1>
        <span class="search-text01">
          <span>
            By Using Jikan and My Own Scraping API, Ive Created the Best
          </span>
          <br />
          <span>Anime Database.</span>
        </span>
      </div>
      <div class="search-container2">
        <input
          type="text"
          required="true"
          placeholder="Search Anime, (X Characters)"
          class="search-input input"
          v-model='query' 
          @keyup='getResult(query)'
          @input="onQueryChange"
        />
      <button type="submit" class="search-button button">
          <span>
            <span>Search</span>
            <br />
            <span></span>
          </span>
        </button>  
      </div>
    </div>
    <div class="search-popular-section">
      <div class="search-container3">
        <h1 class="search-text09"><span>Search Result</span></h1>
        <span class="search-text11">{{query}}</span>
      </div>
      <div class="search-container4">
        <div class="card-feature-card" v-for='result in results' :key='result.title'>
        <img alt="image_alt" class="card-image" :src='result.image_url' width='225px' height="318px"/>
        <h2 class="card-text">{{ result.title }}</h2>
        <router-link :to="'/anime/' + result.mal_id" class="mt">Go</router-link>
        </div>
      </div>
    </div>
    <app-footer></app-footer>
  </main>
</template>

<script>
import AppNavbar from '../components/navbar'
import AppCard from '../components/card'
import AppFooter from '../components/footer'


import axios from 'axios'
import _ from 'lodash'

export default {
  name: 'Search',
  components: {
    AppNavbar,
    AppCard,
    AppFooter,
  },
  data () {
    return {
      query: '',
      results: '',
    }
  },
  head: {
    title: 'Search - nanidb',
    meta: [
      {
        property: 'og:title',
        content: 'Search - nanidb',
      },
    ],
  },
  methods: {
    getResult: _.debounce(
      function(query) {
        axios.get('https://api.jikan.moe/v3/search/anime?q=' + query + '&order_by=title&sort=asc&limit=10')
        .then(response => { 
          this.results = response.data.results;
        })
        console.log(query);     
      }, 500),
    onQueryChange(event) {
      if(event.target.value.trim().length === 0) {
        this.results = null;
      }
    }
  }
}
</script>

<style scoped>
.mt{
  margin-top: 1rem;
}

.card-feature-card {
  width: 100%;
  height: 500px;
  display: flex;
  padding: var(--dl-space-space-unit);
  max-width: var(--dl-size-size-maxwidth);
  transition: 0.3s;
  align-items: center;
  border-color: var(--dl-color-gray-black);
  border-width: 1px;
  flex-direction: column;
  justify-content: center;
}
.card-feature-card:hover {
  transform: scale(1.02);
}
.card-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: var(--dl-radius-radius-radius4);
}

.card-text {
  margin-top: var(--dl-space-space-twounits);
  margin-bottom: 0px;
}

.search-container {
  width: 100%;
  display: flex;
  overflow: auto;
  min-height: 100vh;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background-color: #181719;
}
.search-hero {
  width: 100%;
  height: 450px;
  display: flex;
  padding: var(--dl-space-space-threeunits);
  max-width: var(--dl-size-size-maxwidth);
  min-height: 0px;
  align-items: center;
  flex-direction: row;
  justify-content: space-between;
  background-color: #27242C;
}
.search-container1 {
  display: flex;
  margin-right: var(--dl-space-space-twounits);
  padding-right: var(--dl-space-space-threeunits);
  flex-direction: column;
}
.search-text {
  font-size: 3rem;
  max-width: 450px;
}
.search-text01 {
  margin-top: var(--dl-space-space-twounits);
  margin-bottom: var(--dl-space-space-twounits);
}
.search-container2 {
  flex: 0 0 auto;
  width: 455px;
  height: 100%;
  display: flex;
  align-items: center;
  flex-direction: row;
  justify-content: center;
}
.search-input {
  height: var(--dl-size-size-small);
  border-color: var(--dl-color-gray-500);
}
.search-button {
  color: var(--dl-color-gray-white);
  height: var(--dl-size-size-small);
  transition: 0.3s;
  line-height: 1.9;
  margin-left: var(--dl-space-space-unit);
  background-color: var(--dl-color-gray-black);
}
.search-button:hover {
  color: var(--dl-color-gray-black);
  background-color: transparent;
}
.search-popular-section {
  width: 100%;
  display: flex;
  padding: var(--dl-space-space-threeunits);
  max-width: var(--dl-size-size-maxwidth);
  align-self: center;
  flex-direction: column;
  list-style-type: disc;
  list-style-image: none;
  list-style-position: outside;
}
.search-container3 {
  width: 100%;
  height: 43px;
  display: flex;
  align-items: center;
  margin-bottom: var(--dl-space-space-threeunits);
}
.search-text09 {
  width: 232px;
  font-size: 2rem;
  margin-bottom: 0px;
}
.search-text11 {
  color: #969696;
  font-size: 1.5rem;
}
.search-container4 {
  flex: 0 0 auto;
  width: 100%;
  display: grid;
  grid-gap: var(--dl-space-space-twounits);
  align-items: flex-start;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
@media(max-width: 991px) {
  .search-hero {
    flex-direction: column;
  }
  .search-container1 {
    align-items: center;
    margin-right: 0px;
    margin-bottom: var(--dl-space-space-twounits);
    padding-right: 0px;
  }
  .search-text {
    text-align: center;
  }
  .search-text01 {
    text-align: center;
    padding-left: var(--dl-space-space-threeunits);
    padding-right: var(--dl-space-space-threeunits);
  }
  .search-container2 {
    height: 50px;
  }
  .search-text09 {
    align-self: center;
  }
  .search-container4 {
    grid-template-columns: 1fr 1fr;
  }
}
@media(max-width: 767px) {
  .search-hero {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .search-text01 {
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
  .search-container2 {
    width: 100%;
  }
  .search-popular-section {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
}
@media(max-width: 479px) {
  .search-hero {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .search-container1 {
    margin-bottom: var(--dl-space-space-unit);
  }
  .search-container2 {
    width: 329px;
    height: 109px;
    align-items: center;
    flex-direction: column;
  }
  .search-button {
    margin-top: var(--dl-space-space-unit);
    margin-left: 0px;
  }
  .search-popular-section {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .search-container4 {
    grid-gap: var(--dl-space-space-halfunit);
  }
}
</style>
