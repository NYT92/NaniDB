<template>
  <nav class="navigation-links-nav" v-bind:class="rootClassName">
    <nuxt-link to="/character" class="navigation-links-navlink">
      {{ text }}
    </nuxt-link>
    <nuxt-link to="/popular" class="navigation-links-navlink1">
      {{ text1 }}
    </nuxt-link>
    <nuxt-link to="/page" class="navigation-links-navlink2">
      {{ text2 }}
    </nuxt-link>
    <nuxt-link to="/genre" class="navigation-links-navlink2">
      {{ text5 }}
    </nuxt-link>
    <nuxt-link to="/abouts" class="navigation-links-navlink3">
      {{ text3 }}
    </nuxt-link>
    <a
      href="https://aslnk.ml/nanidb"
      target="_blank"
      rel="noreferrer noopener"
      class="navigation-links-link"
    >
      {{ text4 }}
    </a>
  </nav>
</template>

<script>
export default {
  name: 'NavigationLinks',
  props: {
    text1: {
      type: String,
      default: 'Popular',
    },
    text: {
      type: String,
      default: 'Characters',
    },
    rootClassName: String,
    text4: {
      type: String,
      default: 'Github',
    },
    text2: {
      type: String,
      default: 'All Anime',
    },
    text3: {
      type: String,
      default: 'About',
    },
    text5: {
      type: String,
      default: 'Genre',
    },
  },
}
</script>

<style scoped>
.navigation-links-nav {
  flex: 0 0 auto;
  display: flex;
  align-items: center;
  flex-direction: row;
}
.navigation-links-navlink {
  text-decoration: none;
}
.navigation-links-navlink1 {
  margin-left: var(--dl-space-space-twounits);
  text-decoration: none;
}
.navigation-links-navlink2 {
  margin-left: var(--dl-space-space-twounits);
  text-decoration: none;
}
.navigation-links-navlink3 {
  margin-left: var(--dl-space-space-twounits);
  text-decoration: none;
}
.navigation-links-link {
  margin-left: var(--dl-space-space-twounits);
  text-decoration: none;
}
















@media(max-width: 767px) {
  .navigation-links-nav {
    align-items: flex-start;
    flex-direction: column;
  }
  .navigation-links-navlink {
    margin-bottom: var(--dl-space-space-unit);
  }
  .navigation-links-navlink1 {
    margin-left: 0;
    margin-bottom: var(--dl-space-space-unit);
  }
  .navigation-links-navlink2 {
    margin-left: 0;
    margin-bottom: var(--dl-space-space-unit);
  }
  .navigation-links-navlink3 {
    margin-left: 0;
    margin-bottom: var(--dl-space-space-unit);
  }
  .navigation-links-link {
    margin-left: 0;
    margin-bottom: var(--dl-space-space-unit);
  }
}
</style>
