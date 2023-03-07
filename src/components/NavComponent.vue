<template>
  <nav class="nav" :class="{ active: burgerVisibility }">
    <div class="nav__content">
      <button class="nav__close button" @click="handleMenu">X</button>
      <ul class="nav__list list">
        <li class="list__item item">
          <a class="item__link link" href="#">Popular Places</a>
        </li>
        <li class="list__item item">
          <a class="item__link link" href="#">Covid-19</a>
        </li>
        <li class="list__item item">
          <a class="item__link link" href="#">Visa requirements</a>
        </li>
        <li class="list__item item">
          <a class="item__link link" href="#">Embassy data</a>
        </li>
        <li class="list__item item">
          <a class="item__link link" href="#">Customs</a>
        </li>
        <li class="list__item item">
          <a class="item__link link" href="#">FAQs</a>
        </li>
        <li class="list__item item">
          <button class="item__button button">Other countries</button>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  props: ["burgerVisibility"],
  methods: {
    handleMenu() {
      this.$emit("close");
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/Mixins.scss";

.nav {
  &__list {
    @include onDesktop {
      display: flex;
      align-items: center;
      gap: 37px;
    }
  }

  &__content {
    display: flex;
    flex-direction: column;
    align-items: center;
    box-sizing: border-box;
    height: 100vh;
    padding: 20px 0;
    background: #eef7ff;
    padding: 30px 20px;

    @include onDesktop {
      background: none;
      height: auto;
    }
  }

  &__close {
    @include onMobile {
      align-self: flex-end;
    }

    @include onDesktop {
      display: none;
    }
  }

  @include onMobile {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    transform: translateX(-100%);
    transition: transform 0.3s;
  }
}

.list {
  .item {
    list-style: none;

    @include onMobile {
      padding-bottom: 10px;
    }

    &__link {
      @include linkText;
      text-decoration: none;
    }
  }
}

.button {
  background: #ff843f;
  border-radius: 40px;
  padding: 15px 35px;
  border: none;
  @include linkText(white);
}

.active {
  transform: translateX(0);
}
</style>
