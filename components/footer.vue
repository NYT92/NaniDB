<template>
  <footer class="footer-footer" v-bind:class="rootClassName">
    <img :alt="image_alt" :src="image_src" class="footer-image" />
    <span class="footer-text"><span>© 2022 NaniDB ( By NYT92 )</span></span>
    <icon-group rootClassName="rootClassName"></icon-group>
  </footer>
</template>

<script>
import IconGroup from './icon-group'

export default {
  name: 'Footer',
  props: {
    rootClassName: String,
    image_src: {
      type: String,
      default: '/playground_assets/nanidb_trans.svg',
    },
    image_alt: {
      type: String,
      default: 'logo',
    },
  },
  components: {
    IconGroup,
  },
}
</script>

<style scoped>
.footer-footer {
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
.footer-image {
  height: 2rem;
  object-fit: cover;
}



@media(max-width: 767px) {
  .footer-footer {
    padding-left: var(--dl-space-space-twounits);
    padding-right: var(--dl-space-space-twounits);
  }
  .footer-text {
    text-align: center;
    margin-left: var(--dl-space-space-unit);
    margin-right: var(--dl-space-space-unit);
  }
}
@media(max-width: 479px) {
  .footer-footer {
    padding: var(--dl-space-space-unit);
    flex-direction: column;
  }
  .footer-image {
    margin-bottom: var(--dl-space-space-unit);
  }
  .footer-text {
    margin-left: 0px;
    margin-right: 0px;
    margin-bottom: var(--dl-space-space-unit);
  }
}
</style>
