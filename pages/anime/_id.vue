<template>
  <main class="anime-container">
    <app-navbar rootClassName="rootClassName4"></app-navbar>
    <div class="anime-hero">
      <div class="anime-hero" v-if="getAnimeinfo">
      <div class="anime-container1">
        <img
          alt="image"
          :src="getAnimeinfo.image_url"
          class="anime-image"
        />
      </div>
      <div class="anime-container2">
        <div class="anime-container3">
          <h1 class="anime-text">{{getAnimeinfo.title}}</h1>
          <h2 class="anime-text01">{{getAnimeinfo.title_japanese}}</h2>
          <span class="anime-text02">
            Rank : {{getAnimeinfo.rank}}
          </span>
          <span class="anime-text03">
            Score : {{getAnimeinfo.rank}}
          </span>
          <span class="anime-text04">
            Airing in : {{ getAnimeinfo.aired.string }}
          </span>
          <span class="anime-text05">
            Episodes : {{ getAnimeinfo.episodes }}
          </span>
          <span class="anime-text06">
            Status : {{ getAnimeinfo.status }}
          </span>
        </div>
        <span class="anime-text07">Synopsis :</span>
        <span class="anime-text08">
          <span>
            {{getAnimeinfo.synopsis}}
          </span>
        </span>
        <span class="anime-text10">Trailer :</span>
        <iframe :src="'https://cornfiles.ml/player.html?&file=' + getAnimeinfo.trailer_url" class="anime-iframe" allowfullscreen></iframe>
        <div class="anime-btn-group">
          <a class="anime-button button" :href="getAnimeinfo.url">MyAnimeList</a>
        </div>
      </div>
      </div>
    </div>
    <app-footer rootClassName="rootClassName4"></app-footer>
  </main>
</template>

<script>
import AppNavbar from '../../components/navbar'
import AppFooter from '../../components/footer'

export default {
  name: 'anime',
  props: {},
  components: {
    AppNavbar,
    AppFooter,
  },
  data(){
    return {
      getAnimeinfo: null,
      error: null,
    }
  },
  created(){
    fetch("https://api.jikan.moe/v3/anime/" + this.$route.params.id)
      .then(async response => {
        const data = await response.json();
          if (!response.ok) {
            const error = (data && data.error) || response.status;
            return Promise.reject(error);
        }
        this.getAnimeinfo = data;
      })
      .catch(error => {
        this.error = 'nope' + error;
      });
  },
}
</script>

<style scoped>

.anime-container {
  width: 100%;
  display: flex;
  overflow: auto;
  min-height: 100vh;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background-color: #181719;
}
.anime-hero {
  display: flex;
  padding: var(--dl-space-space-fourunits);
  max-width: 100%;
  min-height: 80vh;
  flex-direction: column;
  justify-content: center;
  background-color: var(--dl-color-gray-white);
}
.anime-container1 {
  width: 100%;
  height: 450px;
  display: flex;
  align-items: center;
  margin-bottom: var(--dl-space-space-oneandhalfunits);
  flex-direction: row;
  justify-content: flex-start;
}
.anime-image {
  width: 300px;
  height: 100%;
}
.anime-container2 {
  width: 100%;
  display: flex;
  align-items: flex-start;
  margin-left: 0px;
  flex-direction: column;
  justify-content: flex-start;
}
.anime-container3 {
  display: flex;
  align-items: flex-start;
  flex-direction: column;
  justify-content: flex-start;
}
.anime-text {
  font-size: 3rem;
}
.anime-text01 {
  margin-top: var(--dl-space-space-unit);
  font-weight: 600;
  margin-bottom: var(--dl-space-space-unit);
}
.anime-text02 {
  font-size: 25px;
  text-transform: capitalize;
}
.anime-text03 {
  font-size: 25px;
  text-transform: capitalize;
}
.anime-text04 {
  font-size: 25px;
  text-transform: capitalize;
}
.anime-text05 {
  font-size: 25px;
  text-transform: capitalize;
}
.anime-text06 {
  font-size: 25px;
  text-transform: capitalize;
}
.anime-text07 {
  font-size: 25px;
  margin-top: var(--dl-space-space-unit);
  text-transform: capitalize;
}
.anime-text08 {
  font-size: 1.3rem;
  align-self: flex-start;
  margin-top: var(--dl-space-space-halfunit);
  margin-bottom: var(--dl-space-space-halfunit);
  padding-right: var(--dl-space-space-threeunits);
}
.anime-text10 {
  font-size: 25px;
  margin-top: var(--dl-space-space-unit);
  margin-bottom: var(--dl-space-space-unit);
  text-transform: capitalize;
}
.anime-iframe {
  width: 100%;
  height: 631px;
  align-self: flex-start;
}
.anime-btn-group {
  height: 54px;
  display: flex;
  margin-top: var(--dl-space-space-unit);
  align-items: center;
  margin-bottom: var(--dl-space-space-unit);
  flex-direction: row;
}
.anime-button {
  color: var(--dl-color-gray-white);
  transition: 0.3s;
  padding-top: var(--dl-space-space-unit);
  margin-right: var(--dl-space-space-unit);
  padding-left: var(--dl-space-space-twounits);
  padding-right: var(--dl-space-space-twounits);
  padding-bottom: var(--dl-space-space-unit);
  background-color: var(--dl-color-gray-black);
}
.anime-button:hover {
  transform: scale(1.02);
}
@media(max-width: 991px) {
  .anime-hero {
    padding: var(--dl-space-space-threeunits);
    flex-direction: column;
  }
  .anime-container1 {
    align-self: stretch;
    justify-content: center;
  }
  .anime-image {
    order: 2;
    margin-bottom: 0px;
  }
  .anime-container2 {
    margin-top: var(--dl-space-space-twounits);
    align-items: center;
    margin-left: 0px;
    margin-right: 0px;
    margin-bottom: var(--dl-space-space-twounits);
  }
  .anime-text {
    text-align: center;
  }
  .anime-text01 {
    text-align: center;
  }
  .anime-text08 {
    font-size: medium;
    text-align: left;
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
  .anime-iframe {
    height: 500px;
  }
}
@media(max-width: 767px) {
  .anime-hero {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
    justify-content: center;
  }
  .anime-container1 {
    width: 300px;
    position: relative;
    align-self: center;
    align-items: center;
    margin-bottom: var(--dl-space-space-threeunits);
    justify-content: center;
  }
  .anime-image {
    width: 300px;
    height: 450px;
    align-self: center;
  }
  .anime-container3 {
    width: 100%;
  }
  .anime-iframe {
    height: 378px;
  }
}
@media(max-width: 479px) {
  .anime-hero {
    padding: var(--dl-space-space-twounits);
    justify-content: center;
  }
  .anime-container1 {
    width: 300px;
    height: 450px;
    align-items: center;
    margin-bottom: var(--dl-space-space-unit);
    justify-content: center;
    list-style-type: disc;
    list-style-image: none;
    list-style-position: outside;
  }
  .anime-container2 {
    margin-bottom: var(--dl-space-space-unit);
  }
  .anime-text08 {
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
  .anime-iframe {
    height: 252px;
  }
  .anime-btn-group {
    width: 100%;
    align-items: center;
    flex-direction: row;
    justify-content: center;
  }
  .anime-button {
    margin-right: 0px;
  }
}
</style>