<template>
  <div class="abouts-container">
    <app-navbar rootClassName="rootClassName"></app-navbar>
    <div class="abouts-hero">
      <div class="abouts-container1">
        <h1 class="abouts-text">Helmlo I am a stupid dev....</h1>
        <span class="abouts-text1">
          <span>i am a 15 years old, high school student and spending time</span>
          <br />
          <span>
            learning programming also little bit of music production.....
          </span>
        </span>
      </div>
    </div>
    <div class="abouts-banner">
      <h1 class="abouts-text5"><span>About The Website</span></h1>
      <span class="abouts-text7">
        Using API technology and skill, i decided to build this site and yes it
        was done by myself (c&amp;p code from stkovflow)
      </span>
    </div>
    <app-footer rootClassName="rootClassName"></app-footer>
  </div>
</template>

<script>
import AppNavbar from '../components/navbar'
import AppFooter from '../components/footer'

export default {
  name: 'Abouts',
  components: {
    AppNavbar,
    AppFooter,
  },
  head: {
    title: 'Abouts - nanidb',
    meta: [
      {
        property: 'og:title',
        content: 'Abouts - nanidb',
      },
    ],
  },
}
</script>

<style scoped>
.abouts-container {
  width: 100%;
  display: flex;
  overflow: auto;
  min-height: 100vh;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  background-color: #000000;
}
.abouts-hero {
  width: 100%;
  height: 450px;
  display: flex;
  padding: var(--dl-space-space-threeunits);
  max-width: var(--dl-size-size-maxwidth);
  min-height: 0px;
  align-items: center;
  flex-direction: row;
  justify-content: space-between;
}
.abouts-container1 {
  display: flex;
  margin-right: var(--dl-space-space-twounits);
  padding-right: var(--dl-space-space-threeunits);
  flex-direction: column;
}
.abouts-text {
  font-size: 3rem;
  max-width: 450px;
}
.abouts-text1 {
  margin-top: var(--dl-space-space-twounits);
  margin-bottom: var(--dl-space-space-twounits);
}
.abouts-banner {
  width: 100%;
  display: flex;
  padding: var(--dl-space-space-threeunits);
  align-items: center;
  flex-direction: column;
  justify-content: space-between;
}
.abouts-text5 {
  font-size: 3rem;
  text-align: center;
}
.abouts-text7 {
  max-width: var(--dl-size-size-maxwidth);
  margin-top: var(--dl-space-space-twounits);
  text-align: center;
  margin-bottom: var(--dl-space-space-twounits);
}
@media(max-width: 991px) {
  .abouts-hero {
    flex-direction: column;
  }
  .abouts-container1 {
    align-items: center;
    margin-right: 0px;
    margin-bottom: var(--dl-space-space-twounits);
    padding-right: 0px;
  }
  .abouts-text {
    text-align: center;
  }
  .abouts-text1 {
    text-align: center;
    padding-left: var(--dl-space-space-threeunits);
    padding-right: var(--dl-space-space-threeunits);
  }
  .abouts-text7 {
    max-width: 100%;
  }
}
@media(max-width: 767px) {
  .abouts-hero {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .abouts-text1 {
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
  .abouts-banner {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .abouts-text7 {
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
  }
}
@media(max-width: 479px) {
  .abouts-hero {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
  .abouts-container1 {
    margin-bottom: var(--dl-space-space-unit);
  }
  .abouts-banner {
    padding-top: var(--dl-space-space-twounits);
    padding-left: var(--dl-space-space-unit);
    padding-right: var(--dl-space-space-unit);
    padding-bottom: var(--dl-space-space-twounits);
  }
}
</style>
