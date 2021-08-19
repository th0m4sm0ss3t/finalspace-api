<template>
  <div class="main">
    <h1 class="main__title">Liste des épisodes</h1>
    <section class="main__Section">
      <div
        v-for="episode in episodes"
        :key="episode.id"
        class="main__Section__Card"
      >
        <h2 class="main__Section__Card__title">{{ episode.name }}</h2>
        <p class="main__Section__Card__year">
          Diffusé le : {{ episode.air_date }}
        </p>
        <img
          class="main__Section__Card__img"
          :src="episode.img_url"
          :alt="episode.name"
        />
        <p class="main__Section____infos director">
          Réalisé par : {{ episode.director }}
        </p>
        <p class="main__Section__Card__infos">
          Écrit par : {{ episode.writer }}
        </p>
      </div>
      <GoUpBtn />
    </section>
  </div>
</template>

<script>
import axios from "axios";
import GoUpBtn from "@/components/GoUpBtn.vue";

export default {
  name: "episodesList",
  created() {
    // get the episodes list on page load
    this.getEpisodes();
  },
  components: {
    GoUpBtn,
  },
  data() {
    return {
      episodes: [],
      errorMsg: "",
    };
  },
  methods: {
    getEpisodes() {
      axios
        .get("https://finalspaceapi.com/api/v0/episode")
        .then((response) => {
          console.log(response.data);
          this.episodes = response.data;
        })
        .catch((error) => {
          console.log(error);
          this.errorMsg = "Error retreiving data !";
        });
    },
  },
};
</script>

<style lang="scss">
@import "../scss/vars.scss";

.main {
  color: $black;
  width: 100%;
  display: flex;
  flex-wrap: wrap;

  &__title {
    font-size: $title-size * 1.5;
    font-weight: bold;
    text-transform: uppercase;
    text-align: center;
    width: 100%;
    margin: $gutter * 5 $gutter $gutter;
  }

  &__btn {
    background-color: $yellow;
    border: $yellow 2px solid;
    color: $black;
    padding: $gutter;
    margin: $gutter auto;

    &:hover {
      color: $white;
      cursor: pointer;
    }
  }

  &__Section {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

    &__Card {
      background-color: $yellow;
      width: 30%;
      margin: $gutter;
      padding: $gutter / 3 0;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;

      &__title {
        width: 100%;
        text-align: center;
        padding: $gutter / 2;
        font-weight: bold;
      }

      &__year {
        text-align: center;
        margin-bottom: $gutter / 2;
      }

      &__infos {
        margin: $gutter / 2;
      }

      &__img {
        width: 90%;
      }
    }
  }
}

.director {
  margin-top: $gutter;
}

/* Small screen */
@media only screen and (max-width: 800px) {
  .main {
    &__Section {
      &__Card {
        &__img {
          width: 90%;
          background-size: cover;
        }
      }
    }
  }

}
</style>
