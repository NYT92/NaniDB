<template>
  <header data-role="Header" class="navbar-navbar" v-bind:class="rootClassName">
    <nuxt-link to="/" class="navbar-navlink">
      <img
        :alt="image_alt"
        :src="image_src"
        loading="eager"
        class="navbar-image"
      />
    </nuxt-link>
    <div class="navbar-nav">
      <navigation-links rootClassName="rootClassName15"></navigation-links>
    </div>
    <div data-type="BurgerMenu" class="navbar-burger-menu">
      <button type="button" data-type="BurgerMenu" class="button burgermenu">
        <svg viewBox="0 0 1024 1024" class="navbar-icon">
          <path
            d="M128 554.667h768c23.552 0 42.667-19.115 42.667-42.667s-19.115-42.667-42.667-42.667h-768c-23.552 0-42.667 19.115-42.667 42.667s19.115 42.667 42.667 42.667zM128 298.667h768c23.552 0 42.667-19.115 42.667-42.667s-19.115-42.667-42.667-42.667h-768c-23.552 0-42.667 19.115-42.667 42.667s19.115 42.667 42.667 42.667zM128 810.667h768c23.552 0 42.667-19.115 42.667-42.667s-19.115-42.667-42.667-42.667h-768c-23.552 0-42.667 19.115-42.667 42.667s19.115 42.667 42.667 42.667z"
          ></path>
        </svg>
      </button>
    </div>
    <div data-type="MobileMenu" class="navbar-mobile-menu">
      <div class="navbar-nav1">
        <div class="navbar-container">
          <img :alt="image_alt1" :src="image_src1" class="navbar-image1" />
          <div data-type="CloseMobileMenu" class="navbar-close-mobile-menu">
            <svg viewBox="0 0 1024 1024" class="navbar-icon2">
              <path
                d="M810 274l-238 238 238 238-60 60-238-238-238 238-60-60 238-238-238-238 60-60 238 238 238-238z"
              ></path>
            </svg>
          </div>
        </div>
        <navigation-links rootClassName="rootClassName16"></navigation-links>
      </div>
    </div>
  </header>
</template>

<script>
import NavigationLinks from './navigation-links'

export default {
  name: 'Navbar',
  props: {
    image_alt1: {
      type: String,
      default: 'image',
    },
    rootClassName: String,
    image_alt: {
      type: String,
      default: 'logo',
    },
    image_src1: {
      type: String,
      default: '/playground_assets/nanidb_trans.svg',
    },
    image_src: {
      type: String,
      default: '/playground_assets/nanidbbta_trans.svg',
    },
  },
  components: {
    NavigationLinks,
  },
}
</script>

<style scoped>
.navbar-navbar {
  width: 100%;
  display: flex;
  max-width: var(--dl-size-size-maxwidth);
  align-items: center;
  padding-top: var(--dl-space-space-twounits);
  padding-left: var(--dl-space-space-threeunits);
  padding-right: var(--dl-space-space-threeunits);
  padding-bottom: var(--dl-space-space-twounits);
  justify-content: space-between;
}
.navbar-navlink {
  display: contents;
}
.navbar-image {
  height: 2rem;
  object-fit: cover;
  text-decoration: none;
}
.navbar-nav {
  display: flex;
}
.navbar-burger-menu {
  display: none;
}
.navbar-icon {
  width: var(--dl-size-size-xsmall);
  height: var(--dl-size-size-xsmall);
  display: none;
}
.navbar-mobile-menu {
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100vh;
  display: none;
  padding: 32px;
  z-index: 100;
  position: absolute;
  flex-direction: column;
  justify-content: space-between;
  background-color: #fff;
}
.navbar-nav1 {
  display: flex;
  align-items: flex-start;
  flex-direction: column;
}
.navbar-container {
  width: 100%;
  display: flex;
  align-items: center;
  margin-bottom: var(--dl-space-space-threeunits);
  justify-content: space-between;
}
.navbar-image1 {
  height: 2rem;
}
.navbar-close-mobile-menu {
  display: flex;
  align-items: center;
  justify-content: center;
}
.navbar-icon2 {
  width: var(--dl-size-size-xsmall);
  height: var(--dl-size-size-xsmall);
}



@media(max-width: 991px) {
  .navbar-image {
    height: 2rem;
  }
  .navbar-icon {
    display: flex;
  }
}
@media(max-width: 767px) {
  .navbar-navbar {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .navbar-nav {
    display: none;
  }
  .navbar-burger-menu {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .navbar-icon {
    fill: #ffffff;
    width: 20px;
    height: 20px;
  }
  .navbar-mobile-menu {
    display: none;
    background-color: #161517;
  }
  .navbar-icon2 {
    fill: #ffffff;
  }
}
@media(max-width: 479px) {
  .navbar-navbar {
    padding: var(--dl-space-space-unit);
  }
  .navbar-mobile-menu {
    padding: 16px;
  }
}
</style>
