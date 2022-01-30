<template>
  <main class="index-container">
    <app-navbar></app-navbar>
    <div class="index-hero">
      <div class="index-container1">
        <h1 class="index-text font-bold">Search Any Anime and Characters</h1>
        <span class="index-text01">
          <span>
            By Using Jikan and My Own Scraping API, Ive Created the Best
          </span>
          <br />
          <span>Anime Database.</span>
        </span>
      </div>
      <div class="index-container2">
        <input
          type="text"
          required="true"
          placeholder="Not Functional Yet"
          class="index-input input"
        />
        <a class="index-button button" href="/search">Click here to Search</a>
      </div>
    </div>
    <div class="home-schd-section">
      <div class="index-container3">
        <h1 class="index-text09"><span>Schedule Anime</span></h1>
        <span class="home-text11">{{ day }}</span>
      </div>
     <div class="index-container4">
        <p>Working on it</p>
      </div>
    </div>
    <div class="index-popular-section">
      <div class="index-container3">
        <h1 class="index-text09"><span>Popular Anime</span></h1>
      </div>
      <div class="index-container4">
        <div class="card-feature-card" v-for='data in popular' :key='data.id'>
          <router-link :to="'/anime/' + data.mal_id" class="card-feature-card">
          <img alt="image_alt" class="card-image" :src='data.image_url'/>
          <h2 class="card-text">Rank : {{ data.rank }}</h2>
          <h3 class="card-text">{{ data.title }}</h3>
          </router-link>
        </div>
      </div>
      <div class="index-container5">
        <nuxt-link to="/popular" class="index-navlink button">
          <span class="index-text11">
            <span>All Popular Lists</span>
            <span></span>
          </span>
        </nuxt-link>
      </div>
    </div>
    <div class="index-popular-section">
      <h1 class="index-text14"><span class="">Upcoming Anime</span></h1>
          <div class="index-container4">
            <div class="card-feature-card" v-for='data in upcoming' :key='data.id'>
              <router-link :to="'/anime/' + data.mal_id" class="card-feature-card">
              <img alt="image_alt" class="card-image" :src='data.image_url'/>
              <h2 class="card-text">{{ data.title }}</h2>
              </router-link>
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
import moment from 'moment'

export default {
  name: 'Home',
  components: {
    AppNavbar,
    AppCard,
    AppFooter,
  },
  head: {
    title: 'nanidb',
    meta: [
      {
        property: 'og:title',
        content: 'nanidb',
      },
    ],
  },
  data(){
    return {
      popular: null,
      upcoming: null,
      schedule: null,
      day: [],
      data: [],
    }
  },
  created(){
      const date = moment();
      const day = moment(date).format('dddd');
      this.day = day
  },

  async asyncData() {
    const getPopular = await axios.get(
      'https://api.jikan.moe/v3/top/anime/1/bypopularity'
    );
    const getRecent = await axios.get(
      'https://api.jikan.moe/v3/top/anime/1/upcoming'
    );

    return {
      popular : getPopular.data.top, 
      upcoming: getRecent.data.top,
    };
  }
}
</script>

<style scoped>
.mt{
  margin-top: 1rem;
}

.card-feature-card {
  width: 100%;
  height: 100%;
  display: flex;
  padding: var(--dl-space-space-unit);
  max-width: var(--dl-size-size-maxwidth);
  transition: 0.3s;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background-color: #27242C;
  border-radius: 5px;
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

.index-container {
  width: 100%;
  display: flex;
  overflow: auto;
  min-height: 100vh;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background-color: #181719;
}
.index-hero {
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
.index-container1 {
  display: flex;
  margin-right: var(--dl-space-space-twounits);
  padding-right: var(--dl-space-space-threeunits);
  flex-direction: column;
}
.index-text {
  font-size: 3rem;
  max-width: 450px;
}
.index-text01 {
  margin-top: var(--dl-space-space-twounits);
  margin-bottom: var(--dl-space-space-twounits);
}
.index-container2 {
  flex: 0 0 auto;
  width: 455px;
  height: 100%;
  display: flex;
  align-items: center;
  flex-direction: row;
  justify-content: center;
}
.index-input {
  height: var(--dl-size-size-small);
  border-color: var(--dl-color-gray-500);
}
.index-button {
  color: var(--dl-color-gray-white);
  height: var(--dl-size-size-small);
  transition: 0.3s;
  line-height: 1.9;
  margin-left: var(--dl-space-space-unit);
  background-color: var(--dl-color-gray-black);
}
.index-button:hover {
  color: var(--dl-color-gray-black);
  background-color: transparent;
}
.index-popular-section {
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
.index-container3 {
  width: 100%;
  height: 43px;
  display: flex;
  align-items: center;
  margin-bottom: var(--dl-space-space-threeunits);
}
.index-text09 {
  width: 266px;
  font-size: 2rem;
  margin-bottom: 0px;
}

.home-text11 {
  color: #6d6d6d;
  font-size: 1.6rem;
}

.home-schd-section {
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

.index-container4 {
  flex: 0 0 auto;
  width: 100%;
  display: grid;
  grid-gap: var(--dl-space-space-twounits);
  align-items: flex-start;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
.index-container5 {
  width: 154px;
  height: 37px;
  display: flex;
  align-self: flex-start;
  margin-top: var(--dl-space-space-threeunits);
  align-items: flex-start;
  flex-direction: column;
  justify-content: center;
}
.index-navlink {
  text-decoration: none;
}
.index-text11 {
  font-size: 15px;
}
.index-recent-section {
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
.index-text14 {
  font-size: 2rem;
  margin-bottom: var(--dl-space-space-threeunits);
}
.index-container6 {
  flex: 0 0 auto;
  width: 100%;
  display: grid;
  grid-gap: var(--dl-space-space-twounits);
  align-items: flex-start;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
@media(max-width: 991px) {
  .index-hero {
    flex-direction: column;
  }
  .index-container1 {
    align-items: center;
    margin-right: 0px;
    margin-bottom: var(--dl-space-space-twounits);
    padding-right: 0px;
  }
  .index-text {
    text-align: center;
  }
  .index-text01 {
    text-align: center;
    padding-left: var(--dl-space-space-threeunits);
    padding-right: var(--dl-space-space-threeunits);
  }
  .index-container2 {
    height: 50px;
  }
  .index-text09 {
    align-self: center;
  }
  .index-container4 {
    grid-template-columns: 1fr 1fr;
  }
  .index-container5 {
    height: 38px;
    align-self: flex-start;
    align-items: center;
    justify-content: center;
  }
  .index-text14 {
    align-self: center;
  }
  .index-container6 {
    grid-template-columns: 1fr 1fr;
  }
}
@media(max-width: 767px) {
  .index-hero {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .index-text01 {
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
  .index-container2 {
    width: 100%;
  }
  .index-popular-section {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .index-recent-section {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
}
@media(max-width: 479px) {
  .index-hero {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .index-container1 {
    margin-bottom: var(--dl-space-space-unit);
  }
  .index-container2 {
    width: 329px;
    height: 109px;
    align-items: center;
    flex-direction: column;
  }
  .index-button {
    margin-top: var(--dl-space-space-unit);
    margin-left: 0px;
  }
  .index-popular-section {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .index-container4 {
    grid-gap: var(--dl-space-space-halfunit);
  }
  .index-recent-section {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .index-container6 {
    grid-gap: var(--dl-space-space-halfunit);
  }
}
</style>