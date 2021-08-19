<template>
  <footer class="footer">
    <p class="footer__text">
      Réalisé par
      <a
        href="https://github.com/th0m4sm0ss3t"
        target="_blank"
        class="footer__link"
        >Thomas Mosset</a
      >
      en utilisant l'API
      <a href="https://finalspaceapi.com/" target="_blank" class="footer__link"
        >Final Space</a
      >
      et
      <a href="https://vuejs.org/" target="_blank" class="footer__link"
        >Vue.js</a
      >. (2021)
    </p>
  </footer>
</template>

<script>
export default {
  name: "footer",
};
</script>

<style lang="scss">
@import "../scss/vars.scss";

.footer {
  margin-top: $gutter;
  padding: $gutter;
  color: $black;
  background-color: $yellow;
  display: flex;
  justify-content: center;

  &__link {
    font-weight: bold;
    color: $black;
    text-decoration: none;

    &:hover {
      color: $white;
    }
  }
}
</style>
