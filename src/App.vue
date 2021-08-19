<template>
  <div class="wrapper">
    <div>
      <Header />
      <nav class="nav">
        <button @click="activeTab = 'Home'" class="nav__btn">Accueil</button>
        <button @click="activeTab = 'EpisodesList'" class="nav__btn">
          Épisodes
        </button>
        <button @click="activeTab = 'CharactersList'" class="nav__btn">
          Personnages
        </button>
        <button @click="activeTab = 'LocationList'" class="nav__btn">
          Lieus
        </button>
        <button @click="activeTab = 'Quotes'" class="nav__btn">
          Citations
        </button>
      </nav>
    </div>
    <!-- Dynamic content -->
    <keep-alive>
      <component :is="activeTab" />
    </keep-alive>
    <!-- End dynamic content -->
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Home from "./components/Home.vue";
import EpisodesList from "./components/EpisodesList.vue";
import CharactersList from "./components/CharactersList.vue";
import LocationList from "./components/LocationList.vue";
import Quotes from "./components/Quotes.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Home,
    EpisodesList,
    CharactersList,
    LocationList,
    Quotes,
    Footer,
  },
  data() {
    return {
      activeTab: "Home",
    };
  },
};
</script>

<style lang="scss">
@import "./scss/reset.scss";
@import "./scss/vars.scss";

#app {
  font-family: "Nunito Sans", sans-serif;
}

.wrapper {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: space-between;
}

.nav {
  background-color: $yellow;
  padding: $gutter;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;

  &__btn {
    margin: 0 $gutter;
    background-color: $yellow;
    border: none;
    color: $black;
    padding: $gutter / 2;
    font-weight: bold;
    font-size: $title-size / 1.4;

    &:hover {
      color: $white;
      cursor: pointer;
    }
  }
}
</style>
