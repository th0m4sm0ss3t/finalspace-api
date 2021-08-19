<template>
  <div class="main">
    <h1 class="main__title">Citations</h1>
    <section class="main__Section">
      <div class="main__Section__Card" v-for="quote in quotes" :key="quote.id">
        <h2 class="main__Section__Card__title">" {{ quote.quote }} "</h2>
        <p class="main__Section__Card__infos">Par : {{ quote.by }}</p>
      </div>
      <GoUpBtn />
    </section>
  </div>
</template>

<script>
import axios from "axios";
import GoUpBtn from "@/components/GoUpBtn.vue";

export default {
  name: "Quotes",
  created() {
    this.getAllQuotes();
  },
  components: {
    GoUpBtn,
  },
  data() {
    return {
      quotes: [],
      errorMsg: "",
    };
  },
  methods: {
    getAllQuotes() {
      axios
        .get("https://finalspaceapi.com/api/v0/quote/")
        .then((response) => {
          console.log(response.data);
          this.quotes = response.data;
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
