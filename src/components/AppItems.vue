<template>
  <ul class="app-items">
    <li
      v-for="(clase, index) in clases"
      :key="index"
      :class="[`app-item`, `item-${clase}`]"
      @click="active"
    >
      <img
        v-if="index < 2"
        class="app-item-img-enganche"
        src="@/assets/front-end_enganche.png"
      />
      <img
        :src="require(`@/assets/front-end_icono_${btns[index]}.png`)"
        class="app-item-img-icon"
        :alt="clase"
      />
      <AppItemHomeSubMenu v-if="index === 1" />
    </li>
  </ul>
</template>

<script>
import AppItemHomeSubMenu from "./AppItemHomeSubMenu";
export default {
  name: "AppItems",
  components: {
    AppItemHomeSubMenu,
  },
  props: {
    btns: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      clases: ["search", "home", "mobile"],
    };
  },
  methods: {
    active(e) {
      const self = e.target;
      self.classList.add("active");
      self.addEventListener("animationend", () =>
        self.classList.remove("active")
      );
      this.$emit("activeClass", e.target.classList[1].split("-")[1]);
    },
  },
};
</script>

<style lang="scss" scoped>
.app-items {
  position: relative;
  z-index: 1;

  .app-item,
  .app-item *,
  .app-item::after {
    position: absolute;
    @include transition-ease;
  }

  .app-item {
    cursor: pointer;

    &::after {
      content: "";
      border-radius: 50%;
      opacity: 0;
      background: rgba(0, 0, 0, 0.3);
    }

    &.active::after {
      animation: click 0.3s forwards;
    }

    &.item-search {
      width: 12.7rem;
      height: 10.7rem;
      transform-origin: 15.3rem 13.4rem;
      @include transition-delay-2s;

      &::after {
        width: 7.5rem;
        height: 7.5rem;
        top: 1.6rem;
        left: 2.3rem;
      }

      img {
        &.app-item-img-icon {
          width: 10.3rem;
          top: 0.2rem;
          left: 0.9rem;
          @include transition-delay-2s;
        }

        &.app-item-img-enganche {
          width: 6rem;
          top: 5.6rem;
          left: 7.1rem;
        }
      }
    }

    &.item-home {
      width: 17.5rem;
      height: 17.1rem;
      transform-origin: -2.1rem 18.2rem;
      left: 17.3rem;
      top: -4.7rem;
      @include transition-delay-2s;

      &::after {
        width: 11.7rem;
        height: 11.7rem;
        top: 2.4rem;
        left: 3rem;
      }

      img {
        &.app-item-img-icon {
          width: 16rem;
          top: 2px;
          left: 9px;
          @include transition-delay-2s;
        }

        &.app-item-img-enganche {
          width: 8rem;
          transform: rotate(98deg);
          top: 9.2rem;
          left: -1.5rem;
        }
      }
    }

    &.item-mobile {
      top: 6.7rem;
      left: 8.4rem;

      &::after {
        width: 9.7rem;
        height: 9.7rem;
        top: 2rem;
        left: 1.9rem;
      }

      img.app-item-img-icon {
        width: 13.5rem;
      }
    }
  }
}
</style>
