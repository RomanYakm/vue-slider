<template>
  <header class="header">
    <div class="header__top">
      <div class="header__logo logo">
        <img src="./assets/logo.png" alt="GMT India Logo" />
      </div>
      <button class="header__burger burger" @click="handleMenu"></button>
      <Nav :burgerVisibility="burgerVisibility" @close="handleMenu" />
    </div>
    <h1 class="header__title title">
      Turkey dolor sit amet, consectetur adipiscing elit
    </h1>
  </header>
  <section class="section">
    <h2 class="section__title title--second">Porular Places</h2>
    <p class="section__text text">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Justo est, est
      massa est ridiculus aliquam enim. Id eget adipiscing feugiat mauris, ac
      non at luctus pretium. Purus, vel dui ut dolor commodo, sed. Nec blandit
      et tincidunt euismod diam. Egestas tellus.
    </p>
  </section>
</template>

<script>
import Nav from "./components/NavComponent.vue";

export default {
  name: "App",
  components: { Nav },
  data() {
    return {
      burgerVisibility: false,
    };
  },
  methods: {
    handleMenu() {
      this.burgerVisibility = !this.burgerVisibility;
    },
  },
};
</script>

<style lang="scss">
@import "./scss/Mixins.scss";

.page {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.header {
  @include onMobile {
    height: 100vh;
    background-image: url("./assets/page_background_mobile.png");
    background-size: cover;
    background-repeat: no-repeat;
    background-position-x: center;
  }

  @include onDesktop {
    background-image: url("./assets/page_background.png");
  }

  &__top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 30px 20px;
    background: linear-gradient(
      177.82deg,
      #eff6f8 1.83%,
      rgba(239, 246, 248, 0) 98.17%
    );
  }

  &__title {
    padding: 65px 0 300px 0;
    margin: 0;
  }
}

.burger {
  @include onDesktop {
    display: none;
  }

  background-image: url("./assets/burger-ico.svg");
  height: 12px;
  width: 20px;
  border: none;
}

.section {
  background-color: #eff6f8;

  &__title {
    margin: 0;
  }
}
</style>
