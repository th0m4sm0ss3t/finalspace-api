<template>
  <div class="main">
    <h1 class="main__title">Liste des personnages</h1>
    <section class="main__Section">
      <div
        v-for="character in characters"
        :key="character.id"
        class="main__Section__Card"
      >
        <h2 class="main__Section__Card__title">{{ character.name }}</h2>
        <img
          class="main__Section__Card__img"
          :src="character.img_url"
          :alt="character.name"
        />
        <p class="main__Section__Card__subTitle">Alias :</p>
        <div class="main__Section__Card__list">
          <ul v-if="character.alias.length">
            <li
              v-for="alias in character.alias"
              :key="alias"
              class="main__Section__Card__list__listEl"
            >
              {{ alias }}
            </li>
          </ul>
          <p v-else class="main__Section__Card__list__listEl">Pas d'alias</p>
        </div>
        <p class="main__Section__Card__subTitle">Genre :</p>
        <p class="main__Section__Card__infos">{{ character.gender }}</p>
        <p class="main__Section__Card__subTitle">Espèce :</p>
        <p class="main__Section__Card__infos">{{ character.species }}</p>
        <p class="main__Section__Card__subTitle">Origine :</p>
        <p class="main__Section__Card__infos">{{ character.origin }}</p>
        <p class="main__Section__Card__subTitle">Status :</p>
        <p class="main__Section__Card__infos">{{ character.status }}</p>
        <p class="main__Section__Card__subTitle">Capacités :</p>
        <div class="main__Section__Card__list">
          <ul v-if="character.abilities.length">
            <li
              v-for="ability in character.abilities"
              :key="ability"
              class="main__Section__Card__list__listEl"
            >
              {{ ability }}
            </li>
          </ul>
          <p v-else class="main__Section__Card__list__listEl">
            Pas de capacité particulière
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
  name: "CharactersList",
  created() {
    this.getCharacters();
  },
  components: {
    GoUpBtn,
  },
  data() {
    return {
      characters: [],
      errorMsg: "",
    };
  },
  methods: {
    getCharacters() {
      axios
        .get("https://finalspaceapi.com/api/v0/character/")
        .then((response) => {
          console.log(response.data);
          this.characters = response.data;
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
        min-height: 20rem;
        max-height: 20rem;
      }
    }
  }
}
</style>
