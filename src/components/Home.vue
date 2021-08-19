<template>
  <section class="home">
    <img
      class="home__img"
      src="https://images5.alphacoders.com/105/thumb-1920-1055769.jpg"
      alt="personnages de Final Space pendant un combat dans l'espace"
    />
    <div>
      <p class="home__text">
        Final Space est une série télévisée d'animation américaine créée par
        Olan Rogers dont les épisodes durent 21 minutes.
      </p>
      <p class="home__text">
        La série montre les aventures dans l'espace de Gary, un astronaute
        prisonnier, et de son ami Mooncake, un extraterrestre capable de
        détruire des planètes, dont la force veut être exploitée par un être
        maléfique, le Lord Commander, pour ouvrir une faille vers l’espace fini
        (le "final space", une prison pour des titans) et ainsi faire entrer
        dans l'univers des monstres d'une autre dimension, appelés les Titans.
      </p>
    </div>
  </section>
</template>

<script>
export default {
  name: "Home",
};
</script>

<style lang="scss">
@import "../scss/vars.scss";

.home {
  margin: $gutter;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  color: $black;

  &__img {
    width: 90%;
  }

  &__text {
    margin: $gutter auto;
    width: 90%;
  }
}

/* Small screen */
@media only screen and (max-width: 800px) {
}

/* Medium screen */
@media only screen and (min-width: 801px) {
  .home {
    &__img {
      width: 80%;
    }

    &__text {
      width: 80%;
    }
  }
}

/* Big screen */
@media only screen and (min-width: 1500px) {
  .home {
    margin-top: $gutter * 4;

    &__img {
      width: 50%;
    }

    &__text {
      margin: $gutter auto;
      width: 50%;
    }
  }
}
</style>
