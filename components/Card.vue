<template>
  <nuxt-link :to="`/stories/${source.id}`" class="card">
    <div class="image-container">
      <img class="card__image" :src="`${baseUrl}${source.ImageUrl[0].url}`" />\
    </div>
    <h4 class="card__name">{{ source.author }}</h4>
    <p class="card__text">{{ source.title }}</p>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    source: Object,
  },
  computed: {
    stories() {
      return this.$store.getters['stories/getStory'];
    },
  },
  data() {
    return {
      baseUrl: process.env.baseUrl,
    };
  },
};
</script>

<style scoped>
.card {
  text-decoration: none;
  color: inherit;
  display: block;
  cursor: pointer;
  transition: 0.3s ease;
}

.card:hover {
  color: #121212;
  opacity: 0.8;
}

.image-container {
  width: 100%;
  height: 0;
  position: relative;
  padding-bottom: calc(100%);
  margin: 0;
}

.card__image {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  object-fit: cover;
  max-width: 300px;
  max-height: 300px;
}

.card__name {
  max-width: 90%;
  font-weight: 600;
  font-size: 22px;
  line-height: 22px;
  margin-top: 20px;
}

.card__text {
  max-width: 85%;
  font-weight: normal;
  font-size: 14px;
  line-height: 18px;
  color: #666;
  margin-top: 14px;
}
@media screen and (max-width: 1280px) {
  .card__image {
    max-width: 265px;
    max-height: 265px;
  }

  .card__name {
    margin-top: 16px;
  }

  .card__text {
    max-width: 85%;
    font-size: 14px;
    line-height: 18px;
    margin-top: 14px;
  }
}

@media screen and (max-width: 1280px) {
  .card__name {
    font-size: 18px;
    line-height: 22px;
    margin-top: 12px;
  }

  .card__text {
    max-width: 85%;
    font-size: 13px;
    line-height: 16px;
    /*max-width: 190px;*/
    margin-top: 10px;
  }
}

@media screen and (max-width: 768px) {
  .card__text {
    min-height: 48px;
    margin-top: 12px;
  }

  .card__image {
    max-width: 216px;
    max-height: 216px;
  }
}

@media (max-width: 425px) {
  .card__image {
    max-width: none;
    max-height: none;
  }
  .card__text {
    max-width: 290px;
  }
}

@media screen and (max-width: 320px) {
  .card__text {
    min-height: 32px;
    margin-top: 14px;
  }
}
</style>
