<template>
  <ul class="app-item-home-submenu">
    <li v-for="n in 4" :key="n">
      <img
        :src="require(`@/assets/front-end_subicono_home${n}.png`)"
        :alt="`subicono${n}`"
      />
    </li>
  </ul>
</template>

<script>
export default {
  name: "AppItemHomeSubMenu",
};
</script>

<style lang="scss" scoped>
.app-item-home-submenu {
  position: absolute;
  width: 18rem;
  height: 10rem;
  top: -6rem;
  left: -4.8rem;

  li {
    transform: scale(0);
    @include transition-ease;
    width: 4.4rem;
    height: 4.4rem;
    position: absolute;

    &:nth-of-type(1) {
      top: 6.2rem;
    }

    &:nth-of-type(2) {
      top: 3rem;
      left: 3.5rem;
    }

    &:nth-of-type(3) {
      left: 8.2rem;
      top: 1.8rem;
    }

    &:nth-of-type(4) {
      top: 2.4rem;
      left: 12.9rem;
    }

    img {
      width: 100%;
      height: 100%;
    }
  }
}
</style>
