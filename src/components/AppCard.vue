<template>
  <div class="container">
    <img
      :src="`https://image.tmdb.org/t/p/w400/${info.poster_path}`"
      :alt="info.title"
    />
    <div class="overlay">
      <h2>
        Titolo: <br />
        <span>{{ info.title }}</span>
      </h2>
      <h3>
        Titolo Originale: <br />
        <span>{{ info.original_title }}</span>
      </h3>
      <div class="info">
        Paese:

        <CountryFlag :country="fixFlag(info.original_language)" size="small" />
      </div>
      <div class="info">
        Rating:
        <font-awesome-icon v-for="star in voteStar" icon="fa-star fa-solid" />
        <font-awesome-icon
          v-for="star in 5 - voteStar"
          icon="fa-star fa-regular"
        />
      </div>
      <p class="info">{{ info.overview }}</p>
    </div>
  </div>
</template>

<script>
import CountryFlag from "vue-country-flag-next";

export default {
  name: "AppCard",
  props: {
    info: Object,
  },
  components: {
    CountryFlag,
  },
  methods: {
    fixFlag(lang) {
      if (lang == "en") {
        return "gb";
      }
      if (lang == "ja") {
        return "jp";
      }
    },
  },
  computed: {
    voteStar() {
      return Math.ceil(this.info.vote_average / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  position: relative;
  cursor: pointer;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  //   text-align: center;

  &:hover .overlay {
    opacity: 0.9;
  }

  .overlay {
    padding: 10px;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    opacity: 0;
    background-color: black;
    overflow-y: auto;

    span {
      font-weight: 500;
    }

    h2,
    h3,
    .info {
      padding-top: 10px;
    }
  }
}
</style>
