<template>
  <div class="app-content">
    <div
      v-for="(btn, index) in btns"
      :key="index"
      class="app-content-img-container"
    >
      <img
        :src="require(`@/assets/front-end_info_${btns[index]}.png`)"
        :alt="btns[index]"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "AppContent",
  props: {
    btns: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss" scoped>
.app-content {
  width: 90%;
  max-width: 36rem;
  position: relative;

  &-img-container {
    background-color: #76c1e0;
    padding: 2rem 0;
    height: 19rem;
    text-align: center;
    position: absolute;
    width: 100%;
    opacity: 0;
    transition: opacity 0.5s;
  }

  img {
    height: 100%;
  }
}
</style>
