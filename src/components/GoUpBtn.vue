<template>
  <div class="goUp" @click="goUp">
    <button class="goUp__btn">
      <div>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="icon icon-tabler icon-tabler-chevron-up"
          width="24"
          height="24"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="#ffffff"
          fill="none"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <path stroke="none" d="M0 0h24v24H0z" fill="none" />
          <polyline points="6 15 12 9 18 15" />
        </svg>
      </div>
    </button>
  </div>
</template>

<script>
export default {
  name: "GoUpBtn",
  methods: {
    goUp() {
      window.scrollTo(0, 0);
    },
  },
};
</script>

<style lang="scss">
@import "../scss/vars.scss";

.goUp {
  position: fixed;
  bottom: 20px;
  right: 30px;
  z-index: 99;

  &__btn {
    background-color: $black;
    color: $yellow;
    border: $yellow 2px solid;
    cursor: pointer;

    &:hover {
      background-color: $yellow;
    }
  }
}
</style>
