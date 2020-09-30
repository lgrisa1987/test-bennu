<template>
  <div class="app-descriptions">
    <div
      v-for="description in descriptions"
      :key="description.id"
      class="app-description"
    >
      <div class="lines">
        <span class="circle"></span>
        <span class="line"></span>
        <span class="circle"></span>
      </div>
      <div class="copy">
        <p class="id">{{ description.id }}</p>
        <p class="title">{{ description.title.substring(0, 40) }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppDescripions",
  props: {
    descriptions: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss">
.app {
  &-descriptions {
    position: relative;
    display: block;
  }

  &-description {
    height: 9rem;
    position: absolute;
    display: flex;
    align-items: center;
    width: 10rem;

    p {
      text-align: left;
      &.id {
        font-size: 1.8rem;
      }
      &.title {
        font-size: 1rem;
      }
    }

    &:nth-of-type(1) {
      top: -9rem;
      left: 4rem;
    }

    &:nth-of-type(2) {
      top: 20rem;
      left: 11rem;
    }

    &:nth-of-type(3) {
      top: 12rem;
      left: 22rem;
      flex-direction: row-reverse;
      .copy {
        padding-right: 0.5rem;
        p {
          text-align: right;
        }
      }
    }

    .lines {
      width: 0.5rem;
      height: 100%;

      .circle,
      .line {
        display: block;
        background: white;
      }

      .circle {
        width: 0.5rem;
        height: 0.5rem;
        border-radius: 50%;
        animation: appear 0.3s 0.4s both ease-out;
      }

      .line {
        width: 0.1rem;
        margin: 0.2rem auto;
        animation: height 0.4s 0.5s both ease-out;
        @include ie11 {
          position: relative;
          left: 1px;
        }

        & + .circle {
          animation-delay: 0.8s;
        }
      }
    }
    .copy {
      padding-left: 0.5rem;
      animation: appear 0.3s 0.4s both ease-out;
    }
  }
}
</style>
