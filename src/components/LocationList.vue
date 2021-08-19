<template>
  <div class="main">
    <h1 class="main__title">Liste des lieus</h1>
    <section class="main__Section">
      <div
        v-for="location in locations"
        :key="location.id"
        class="main__Section__Card"
      >
        <h2 class="main__Section__Card__title">{{ location.name }}</h2>
        <img
          class="main__Section__Card__img"
          :src="location.img_url"
          :alt="location.name"
        />
        <p class="main__Section__Card__subTitle">Type :</p>
        <p class="main__Section__Card__infos">{{ location.type }}</p>
        <p class="main__Section__Card__subTitle">Habitant·es :</p>
        <div class="main__Section__Card__list">
          <ul v-if="location.inhabitants.length">
            <li
              v-for="inhabitant in location.inhabitants"
              :key="inhabitant"
              class="main__Section__Card__list__listEl"
            >
              {{ inhabitant }}
            </li>
          </ul>
          <p v-else class="main__Section__Card__list__listEl">
            Pas d'habitant·es connu·es
          </p>
        </div>
      </div>
      <GoUpBtn />
    </section>
  </div>
</template>

<script>
import axios from "axios";
import GoUpBtn from "@/components/GoUpBtn.vue";

export default {
  name: "LocationList",
  created() {
    this.getLocations();
  },
  components: {
    GoUpBtn,
  },
  data() {
    return {
      locations: [],
      errorMsg: "",
    };
  },
  methods: {
    getLocations() {
      axios
        .get("https://finalspaceapi.com/api/v0/location/")
        .then((response) => {
          console.log(response.data);
          this.locations = response.data;
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

    @media only screen and (max-width: 950px) {
      justify-content: center;
    }

    &__Card {
      background-color: $yellow;
      width: 30%;
      margin: $gutter;
      padding: $gutter / 3 0;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;

      @media only screen and (max-width: 950px) {
        width: 60%;
      }

      &__title {
        width: 100%;
        text-align: center;
        padding: $gutter / 2;
        font-weight: bold;
        font-size: $title-size;
      }

      &__subTitle {
        background-color: $black;
        color: $white;
        width: 80%;
        text-align: center;
        padding: $gutter / 2 0;
        margin-top: $gutter;
      }

      &__list {
        width: 100%;
        text-align: center;
        margin: $gutter / 2 0;

        &__listEl {
          margin-top: $gutter / 2;
        }
      }

      &__infos {
        width: 100%;
        margin: $gutter / 2;
        text-align: center;
      }

      &__img {
        width: 90%;
        height: auto;
      }
    }
  }
}
</style>
