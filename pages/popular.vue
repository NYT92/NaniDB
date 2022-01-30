<template>
  <main class="popular-container">
    <app-navbar rootClassName="rootClassName2"></app-navbar>
    <div class="popular-hero">
      <div class="popular-container1">
        <h1 class="popular-text">Search Any Anime and Characters</h1>
        <span class="popular-text01">
          <span>
            By Using Jikan and My Own Scraping API, Ive Created the Best
          </span>
          <br />
          <span>Anime Database.</span>
        </span>
      </div>
      <div class="popular-container2">
        <input
          type="text"
          required="true"
          placeholder="Search Anime, Characters"
          class="popular-input input"
        />
        <button class="popular-button button">
          <span>
            <span>Search</span>
            <br />
            <span></span>
          </span>
        </button>
      </div>
    </div>
    <div class="popular-popular-section">
      <div class="popular-container3">
        <h1 class="popular-text09"><span>Popular Anime</span></h1>
      </div>
      <div class="popular-container4">
        <div class="card-feature-card" v-for='result in results' :key='result.title'>
          <img alt="image_alt" class="card-image" :src='result.image_url' width='225px' height="318px"/>
          <h2 class="card-text">Top {{ result.rank }}{{ result.title }}</h2>
          <a :href='result.url'>Go</a>
        </div>
      </div>
    </div>
    <div class="popular-container6">
        <div class="btn-group">
        <button class="btn">1</button> 
        <button class="btn btn-active">2</button> 
        <button class="btn">3</button> 
        <button class="btn">4</button> 
      </div>
    </div>
    <app-footer rootClassName="rootClassName2"></app-footer>
  </main>
</template>

<script>
import AppNavbar from '../components/navbar'
import AppCard from '../components/card'
import AppFooter from '../components/footer'

import axios from 'axios'

export default {
  name: 'Popular',
  components: {
    AppNavbar,
    AppCard,
    AppFooter,
  },
  head: {
    title: 'Popular - nanidb',
    meta: [
      {
        property: 'og:title',
        content: 'Popular - nanidb',
      },
    ],
  },
  data () {
    return {
      results: '',
    }
  },
  methods: {
     getUnits: function() {
      axios.get('https://api.jikan.moe/v3/top/anime/1/upcoming')
        .then(res => { 
          this.results = res.data.results;
        })
      console.log(this.results)
     }
  },
  beforeMount() {
      this.getUnits()
  }
}
</script>

<style scoped>
.popular-container {
  width: 100%;
  display: flex;
  overflow: auto;
  min-height: 100vh;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background-color: #181719;
}
.popular-hero {
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
.popular-container1 {
  display: flex;
  margin-right: var(--dl-space-space-twounits);
  padding-right: var(--dl-space-space-threeunits);
  flex-direction: column;
}
.popular-text {
  font-size: 3rem;
  max-width: 450px;
}
.popular-text01 {
  margin-top: var(--dl-space-space-twounits);
  margin-bottom: var(--dl-space-space-twounits);
}
.popular-container2 {
  flex: 0 0 auto;
  width: 455px;
  height: 100%;
  display: flex;
  align-items: center;
  flex-direction: row;
  justify-content: center;
}
.popular-input {
  height: var(--dl-size-size-small);
  border-color: var(--dl-color-gray-500);
}
.popular-button {
  color: var(--dl-color-gray-white);
  height: var(--dl-size-size-small);
  transition: 0.3s;
  line-height: 1.9;
  margin-left: var(--dl-space-space-unit);
  background-color: var(--dl-color-gray-black);
}
.popular-button:hover {
  color: var(--dl-color-gray-black);
  background-color: transparent;
}
.popular-popular-section {
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
.popular-container3 {
  width: 100%;
  height: 35px;
  display: flex;
  align-items: flex-start;
  margin-bottom: var(--dl-space-space-threeunits);
}
.popular-text09 {
  font-size: 2rem;
  margin-bottom: 0px;
}
.popular-container4 {
  flex: 0 0 auto;
  width: 100%;
  display: grid;
  grid-gap: var(--dl-space-space-twounits);
  align-items: flex-start;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
.popular-container5 {
  flex: 0 0 auto;
  width: 100%;
  display: grid;
  grid-gap: var(--dl-space-space-twounits);
  margin-top: var(--dl-space-space-oneandhalfunits);
  align-items: flex-start;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
.popular-container6 {
  flex: 0 0 auto;
  width: 200px;
  height: 100px;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}
.popular-text11 {
  font-size: 32px;
}
@media(max-width: 991px) {
  .popular-hero {
    flex-direction: column;
  }
  .popular-container1 {
    align-items: center;
    margin-right: 0px;
    margin-bottom: var(--dl-space-space-twounits);
    padding-right: 0px;
  }
  .popular-text {
    text-align: center;
  }
  .popular-text01 {
    text-align: center;
    padding-left: var(--dl-space-space-threeunits);
    padding-right: var(--dl-space-space-threeunits);
  }
  .popular-container2 {
    height: 50px;
  }
  .popular-text09 {
    align-self: center;
  }
  .popular-container4 {
    grid-template-columns: 1fr 1fr;
  }
  .popular-container5 {
    grid-template-columns: 1fr 1fr;
  }
}
@media(max-width: 767px) {
  .popular-hero {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .popular-text01 {
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
  .popular-container2 {
    width: 100%;
  }
  .popular-popular-section {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
}
@media(max-width: 479px) {
  .popular-hero {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .popular-container1 {
    margin-bottom: var(--dl-space-space-unit);
  }
  .popular-container2 {
    width: 329px;
    height: 109px;
    align-items: center;
    flex-direction: column;
  }
  .popular-button {
    margin-top: var(--dl-space-space-unit);
    margin-left: 0px;
  }
  .popular-popular-section {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .popular-container4 {
    grid-gap: var(--dl-space-space-halfunit);
  }
  .popular-container5 {
    grid-gap: var(--dl-space-space-halfunit);
  }
}
</style>
