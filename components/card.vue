<template>
  <div class="card-feature-card" v-bind:class="rootClassName">
    <img :alt="image_alt" :src="image_src" class="card-image" />
    <h2 class="card-text">{{ title }}</h2>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    rootClassName: String,
    image_src: {
      type: String,
      default:
        'https://images.unsplash.com/photo-1512295767273-ac109ac3acfa?ixid=Mnw5MTMyMXwwfDF8c2VhcmNofDF8fHllbGxvdyUyMHRlY2h8ZW58MHx8fHwxNjI2MjU1NDk0&ixlib=rb-1.2.1&w=1000',
    },
    image_alt: {
      type: String,
      default: 'image',
    },
    title: {
      type: String,
      default: 'Lorem ipsum',
    },
  },
}
</script>

<style scoped>
.card-feature-card {
  width: 100%;
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
  width: var(--dl-size-size-medium);
  height: var(--dl-size-size-medium);
  object-fit: cover;
  border-radius: var(--dl-radius-radius-radius4);
}
.card-text {
  margin-top: var(--dl-space-space-twounits);
  margin-bottom: 0px;
}
































































































</style>
