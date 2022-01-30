<template>
  <main class="character-container">
    <app-navbar rootClassName="rootClassName4"></app-navbar>
    <div class="character-hero" v-if="getCharinfo">
      <div class="character-hero">
        <div class="character-container1">
        <img
          alt="image"
          class="character-image"
          :src='getCharinfo.image_url'
        />
      </div>
      <div class="character-container2">
        <div class="character-container3">
          <h1 class="character-text">{{getCharinfo.name}}</h1>
          <h2 class="character-text1">{{getCharinfo.name_kanji}}</h2>
        </div>
        <span class="character-text2">About :</span>
        <span class="character-text3">
          <span>{{getCharinfo.about}}</span>
        </span>
        <div class="character-btn-group">
          <a class="character-button button" :href='getCharinfo.url'>MyAnimeList</a>
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
  name: 'Character',
  props: {},
  components: {
    AppNavbar,
    AppFooter,
  },
  data(){
    return {
      getCharinfo: null,
      error: null,
    }
  },
  created(){
    fetch("https://api.jikan.moe/v3/character/" + this.$route.params.id)
      .then(async response => {
        const data = await response.json();
          if (!response.ok) {
            const error = (data && data.error) || response.status;
            return Promise.reject(error);
        }
        this.getCharinfo = data;
      })
      .catch(error => {
        this.error = 'nope' + error;
      });
  },
}
</script>

<style scoped>
.character-container {
  width: 100%;
  display: flex;
  overflow: auto;
  min-height: 100vh;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background-color: #181719;
}
.character-hero {
  display: flex;
  padding: var(--dl-space-space-fourunits);
  max-width: 100%;
  min-height: 80vh;
  flex-direction: column;
  justify-content: center;
  background-color: var(--dl-color-gray-white);
}
.character-container1 {
  width: 100%;
  height: 450px;
  display: flex;
  align-items: center;
  margin-bottom: var(--dl-space-space-oneandhalfunits);
  flex-direction: row;
  justify-content: flex-start;
}
.character-image {
  width: 300px;
  height: 100%;
}
.character-container2 {
  width: 100%;
  display: flex;
  align-items: flex-start;
  margin-left: 0px;
  flex-direction: column;
  justify-content: flex-start;
}
.character-container3 {
  display: flex;
  align-items: flex-start;
  flex-direction: column;
  justify-content: flex-start;
}
.character-text {
  font-size: 3rem;
}
.character-text1 {
  margin-top: var(--dl-space-space-unit);
  font-weight: 600;
  margin-bottom: var(--dl-space-space-unit);
}
.character-text2 {
  font-size: 25px;
  margin-top: var(--dl-space-space-unit);
  text-transform: capitalize;
}
.character-text3 {
  font-size: 1.3rem;
  align-self: flex-start;
  margin-top: var(--dl-space-space-halfunit);
  margin-bottom: var(--dl-space-space-halfunit);
  padding-right: var(--dl-space-space-threeunits);
}
.character-btn-group {
  height: 54px;
  display: flex;
  margin-top: var(--dl-space-space-unit);
  align-items: center;
  margin-bottom: var(--dl-space-space-unit);
  flex-direction: row;
}
.character-button {
  color: var(--dl-color-gray-white);
  transition: 0.3s;
  padding-top: var(--dl-space-space-unit);
  margin-right: var(--dl-space-space-unit);
  padding-left: var(--dl-space-space-twounits);
  padding-right: var(--dl-space-space-twounits);
  padding-bottom: var(--dl-space-space-unit);
  background-color: var(--dl-color-gray-black);
}
.character-button:hover {
  transform: scale(1.02);
}
@media(max-width: 991px) {
  .character-hero {
    padding: var(--dl-space-space-threeunits);
    flex-direction: column;
  }
  .character-container1 {
    align-self: stretch;
    justify-content: center;
  }
  .character-image {
    order: 2;
    margin-bottom: 0px;
  }
  .character-container2 {
    margin-top: var(--dl-space-space-twounits);
    align-items: center;
    margin-left: 0px;
    margin-right: 0px;
    margin-bottom: var(--dl-space-space-twounits);
  }
  .character-text {
    text-align: center;
  }
  .character-text1 {
    text-align: center;
  }
  .character-text3 {
    font-size: medium;
    text-align: left;
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
}
@media(max-width: 767px) {
  .character-hero {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
    justify-content: center;
  }
  .character-container1 {
    width: 300px;
    position: relative;
    align-self: center;
    align-items: center;
    margin-bottom: var(--dl-space-space-threeunits);
    justify-content: center;
  }
  .character-image {
    width: 300px;
    height: 450px;
    align-self: center;
  }
  .character-container3 {
    width: 100%;
  }
}
@media(max-width: 479px) {
  .character-hero {
    padding: var(--dl-space-space-twounits);
    justify-content: center;
  }
  .character-container1 {
    width: 300px;
    height: 450px;
    align-items: center;
    margin-bottom: var(--dl-space-space-unit);
    justify-content: center;
    list-style-type: disc;
    list-style-image: none;
    list-style-position: outside;
  }
  .character-container2 {
    margin-bottom: var(--dl-space-space-unit);
  }
  .character-text3 {
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
  .character-btn-group {
    width: 100%;
    align-items: center;
    flex-direction: row;
    justify-content: center;
  }
  .character-button {
    margin-right: 0px;
  }
}
</style>
