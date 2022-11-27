<template>
  <header class="header">
    <div class="header__inner">
      <a href="#">
        <img
          src="src/assets/img/icons/logo.svg"
          alt="logo"
          class="header__logo"
          :class="{ active: isOpen }"
        />
      </a>
      <div class="header__group" :class="{ active: isOpen }">
        <img src="src/assets/img/icons/header-user.svg" alt="icon-user" />
        <img src="src/assets/img/icons/header-heart.svg" alt="icon-heart" />
        <img src="src/assets/img/icons/header-cart.svg" alt="icon-cart" />
        <button
          class="header__burger burger"
          :class="{ active: isOpen }"
          @click="toggle"
        >
          <span class="burger__bar burger__bar_1"></span>
          <span class="burger__bar burger__bar_2"></span>
          <span class="burger__bar burger__bar_3"></span>
        </button>
      </div>
      <div class="header__menu" :class="{ active: isOpen }">gfdgdf</div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
      windowWidth: null,
    };
  },
  mounted() {
    window.addEventListener("resize", this.isResize);
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.isResize);
  },
  methods: {
    toggle() {
      this.isOpen = !this.isOpen;
    },
    isResize() {
      this.windowWidth = window.innerWidth;
      if (this.windowWidth >= 1024) {
        this.isOpen = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  background: #ffffff;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  padding: 12px 0;
  &__inner {
    @include container;
    display: flex;
    justify-content: space-between;
  }
  &__logo {
    transform: translateX(0);
    transition: 0.3s ease-in-out;
  }
  &__group {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 30px;
    align-items: center;
  }
  .burger {
    position: relative;
    height: 18px;
    width: 32px;
    display: none;
    pointer-events: all;
    transition: 0.3s ease-in-out;
    &.active .burger__bar {
      &_1 {
        transform: rotate(45deg);
      }

      &_2 {
        opacity: 0;
      }

      &_3 {
        transform: rotate(-45deg);
      }
    }
    &:hover .burger__bar_2 {
      transform: scaleX(0.8);
    }
    &:focus {
      outline: 0;
    }
    &__bar {
      background-color: #333333;
      position: absolute;
      top: 50%;
      right: 6px;
      left: 6px;
      height: 1px;
      width: auto;
      transition: 0.3s ease-in-out;
      &_1 {
        transform: translateY(-6px);
      }

      &_2 {
        transform-origin: 100% 50%;
        transform: scaleX(1);
      }
      &_3 {
        transform: translateY(6px);
      }
    }
  }
  &__menu {
    @include container;
    transform: translateX(-100%);
    position: absolute;
    background: #ffffff;
    top: 40px;
    left: 0;
    width: 100%;
    height: 300px;
    transition: 0.3s ease-in-out;
    &.active {
      transform: translateX(0);
    }
  }
  @include _1024 {
    .burger {
      display: block;
    }
    &__group {
      grid-template-columns: 1fr 1fr 1fr 1fr;
      grid-gap: 20px;
      &.active {
        grid-template-columns: 1fr;
        grid-gap: 20px;

        img {
          display: none;
        }
      }
    }
    &__logo.active {
      transform: translateX(-1000%);
    }
  }
}
</style>
