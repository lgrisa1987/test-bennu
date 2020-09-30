<template>
  <div class="app">
    <h1>Lorem Ipsum</h1>
    <div class="app-main-content">
      <div :class="['app-navigation', active]">
        <AppDescriptions :descriptions="descriptions" />
        <AppItems :btns="btns" @activeClass="activeClass" />
      </div>
      <AppContent :btns="btns" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AppDescriptions from "./components/AppDescriptions";
import AppItems from "./components/AppItems";
import AppContent from "./components/AppContent";
export default {
  name: "App",
  components: {
    AppDescriptions,
    AppItems,
    AppContent,
  },
  data() {
    return {
      descriptions: [],
      btns: ["buscar", "home", "celus"],
      active: "active-mobile",
    };
  },
  created() {
    this.getDynamicData();
  },
  methods: {
    getDynamicData() {
      axios
        .get("https://jsonplaceholder.typicode.com/posts?_limit=3")
        .then((response) => (this.descriptions = response.data))
        .catch((error) => console.log(error));
    },
    activeClass(value) {
      this.active = `active-${value}`;
    },
  },
};
</script>

<style lang="scss">
.app {
  padding: 3rem 0;
  text-align: center;
  animation: appear 0.5s 0.3s both;

  &-main-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: auto;

    @include breakpoint(800px) {
      padding: 0 2rem;
      max-width: 90rem;
      flex-direction: row;
      justify-content: space-between;
    }
  }

  &-navigation {
    width: 100%;
    padding-top: 13rem;
    max-width: 37rem;
    height: 46rem;
    position: relative;
    @include breakpoint(800px) {
      height: 35rem;
    }

    &.active-search .app-descriptions,
    &.active-home .app-descriptions {
      display: none;
    }

    &.active-search {
      .app-item.item-search {
        transform: rotate(45deg);

        img.app-item-img-icon {
          transform: rotate(-45deg);
        }
      }

      .app-item.item-home {
        transform: rotate(80deg);

        img.app-item-img-icon {
          transform: rotate(-80deg);
        }
      }

      & + .app-content .app-content-img-container:first-of-type {
        opacity: 1;
        @include transition-delay-4s;
      }
    }

    &.active-home {
      .app-item.item-search {
        transform: rotate(-80deg);

        img.app-item-img-icon {
          transform: rotate(80deg);
        }
      }

      .app-item.item-home {
        transform: rotate(15deg);

        img.app-item-img-icon {
          transform: rotate(-15deg);
        }
      }

      .app-item.item-home .app-item-home-submenu {
        transform: rotate(-15deg);

        li {
          transform: scale(1);
          transition-delay: 0.4s;
        }
      }

      & + .app-content .app-content-img-container:nth-of-type(2) {
        opacity: 1;
        @include transition-delay-4s;
      }
    }
    &.active-mobile {
      & + .app-content .app-content-img-container:last-of-type {
        opacity: 1;
        @include transition-delay-4s;
      }
    }
  }
}
</style>
