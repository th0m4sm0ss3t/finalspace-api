<template>
  <header class="header">
    <img src="../assets/finalspace.png" alt="Mooncake" class="header__logo" />
    <h1 class="header__title">Final Space</h1>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss">
@import "../scss/vars.scss";

.header {
  background-image: url(https://images.unsplash.com/photo-1588894167282-408680bb62f4?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=678&q=80);
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  padding: $gutter;

  &__title {
    text-align: center;
    font-size: $title-size * 3;
    padding: $gutter;
    font-weight: bold;
    text-transform: uppercase;
    color: $white;
  }

  &__logo {
    width: 25%;

    @media only screen and (min-width: 950px) {
      width: 10%;
    }
  }
}
</style>
