<template>
  <div class="app-component-container">
    <app-navbar rootClassName="rootClassName5"></app-navbar>
    <div class="app-component-hero">
      <div class="app-component-container1">
        <div class="app-component-container2">
          <div class="app-component-container3">
            <h1 class="app-component-text" v-if="error.statusCode === 404">
              404 Not Found..
            </h1>
            <h1 class="app-component-text" v-else>
              Error
            </h1>
          </div>
          <svg viewBox="0 0 1024 1024" class="app-component-icon">
            <path
              d="M1024 576v-64h-193.29c-5.862-72.686-31.786-139.026-71.67-192.25h161.944l70.060-280.24-62.090-15.522-57.94 231.76h-174.68c-0.892-0.694-1.796-1.374-2.698-2.056 6.71-19.502 10.362-40.422 10.362-62.194 0.002-105.76-85.958-191.498-191.998-191.498s-192 85.738-192 191.5c0 21.772 3.65 42.692 10.362 62.194-0.9 0.684-1.804 1.362-2.698 2.056h-174.68l-57.94-231.76-62.090 15.522 70.060 280.24h161.944c-39.884 53.222-65.806 119.562-71.668 192.248h-193.29v64h193.37c3.802 45.664 15.508 88.812 33.638 127.75h-123.992l-70.060 280.238 62.090 15.524 57.94-231.762h112.354c58.692 78.032 147.396 127.75 246.66 127.75s187.966-49.718 246.662-127.75h112.354l57.94 231.762 62.090-15.524-70.060-280.238h-123.992c18.13-38.938 29.836-82.086 33.636-127.75h193.37z"
            ></path>
          </svg>
        </div>
        <span class="app-component-text1"><span>Wrong Page Dude....</span></span>
      </div>
      <img
        alt="image"
        src="/playground_assets/nanidb_trans.svg"
        loading="lazy"
        class="app-component-image"
      />
    </div>
    <app-footer rootClassName="rootClassName5"></app-footer>
  </div>
</template>

<script>
import AppNavbar from '../components/navbar'
import AppFooter from '../components/footer'

export default {
  name: 'AppComponent',
  props: ['error'],
  components: {
    AppNavbar,
    AppFooter,
  },
  layout: 'error',
}
</script>

<style scoped>
.app-component-container {
  width: 100%;
  display: flex;
  overflow: auto;
  min-height: 100vh;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background-color: #000000;
}
.app-component-hero {
  width: 100%;
  height: 812px;
  display: flex;
  padding: var(--dl-space-space-threeunits);
  max-width: var(--dl-size-size-maxwidth);
  min-height: 0px;
  align-items: center;
  flex-direction: row;
  justify-content: space-between;
}
.app-component-container1 {
  display: flex;
  margin-right: var(--dl-space-space-twounits);
  padding-right: var(--dl-space-space-threeunits);
  flex-direction: column;
}
.app-component-container2 {
  flex: 0 0 auto;
  width: auto;
  height: auto;
  display: flex;
  align-items: flex-start;
}
.app-component-container3 {
  flex: 0 0 auto;
  width: auto;
  height: auto;
  display: flex;
  align-items: flex-start;
}
.app-component-text {
  font-size: 3rem;
  max-width: 450px;
}
.app-component-icon {
  fill: #fff5f5;
  width: 63px;
  height: 60px;
}
.app-component-text1 {
  margin-top: var(--dl-space-space-twounits);
  margin-bottom: var(--dl-space-space-twounits);
}
.app-component-image {
  width: 496px;
  height: 436px;
}
@media(max-width: 991px) {
  .app-component-hero {
    flex-direction: column;
  }
  .app-component-container1 {
    align-items: center;
    margin-right: 0px;
    margin-bottom: 0px;
    padding-right: 0px;
  }
  .app-component-text {
    text-align: center;
  }
  .app-component-text1 {
    text-align: center;
    padding-left: var(--dl-space-space-threeunits);
    padding-right: var(--dl-space-space-threeunits);
  }
  .app-component-image {
    height: 581px;
  }
}
@media(max-width: 767px) {
  .app-component-hero {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .app-component-text1 {
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
}
@media(max-width: 479px) {
  .app-component-hero {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .app-component-container1 {
    margin-bottom: var(--dl-space-space-unit);
  }
}
</style>
