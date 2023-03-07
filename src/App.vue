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
      <span class="title__first-word">Turkey</span> dolor sit amet, consectetur
      adipiscing elit
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
    <div class="glide">
      <div data-glide-el="track" class="glide__track">
        <ul class="glide__slides">
          <li class="glide__slide">
            <img
              class="glide__image"
              src="./assets/slider/popular-places-slide-1.jpg"
              alt=""
            />
            <p class="glide__text">Arga</p>
          </li>
          <li class="glide__slide">
            <img
              class="glide__image"
              src="./assets/slider/popular-places-slide-2.jpg"
              alt=""
            />
            <p class="glide__text">Arga2</p>
          </li>
          <li class="glide__slide">
            <img
              class="glide__image"
              src="./assets/slider/popular-places-slide-3.jpg"
              alt=""
            />
            <p class="glide__text">Arga3</p>
          </li>
        </ul>
      </div>
      <div class="glide__bullets" data-glide-el="controls[nav]">
        <button class="glide__bullet" data-glide-dir="=0">1</button>
        <button class="glide__bullet" data-glide-dir="=1">2</button>
        <button class="glide__bullet" data-glide-dir="=2">3</button>
      </div>
    </div>
  </section>
</template>

<script>
import Glide from "@glidejs/glide";
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
  mounted() {
    new Glide(".glide").mount();
  },
};
</script>

<style lang="scss">
@import "node_modules/@glidejs/glide/src/assets/sass/glide.core";
@import "./scss/Mixins.scss";
@import "./scss/Fonts.scss";

.page {
  margin: 0;
}

#app {
  font-family: "Raleway";
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
    font-family: "MuseoSansBlack";
    padding: 65px 20px 300px 20px;
    margin: 0;
    text-align: left;
  }
}

.title {
  &__first-word {
    color: #ff843f;
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
    @include sectionTitle;
    margin: 0;
  }

  &__text {
    @include sectionText;
    margin: 0;
    padding-bottom: 30px;
  }
}

.glide {
  &__slide {
    position: relative;
    text-align: center;
  }

  &__image {
    width: 275px;
    height: 275px;
    filter: drop-shadow(10px 10px 20px rgba(2, 72, 115, 0.2));
    border-radius: 30px;
  }

  &__text {
    @include textOnImgSlide;
    position: absolute;
    bottom: 8px;
    left: 75px;
    color: white;
  }
}
</style>
