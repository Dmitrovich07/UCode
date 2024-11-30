<template>
  <header id="header-section">
    <div class="container">
      <div class="header">
        <h1 class="header__logo">
          <span class="header__logo_green">U</span>-Coda
        </h1>
        <ul class="header__menu" :class="{ open: isOpen }">
          <li class="menu-link__item">
            <router-link to="/" class="menu-link" @click="toggleBurger">Home</router-link>
          </li>
          <li class="menu-link__item">
            <router-link to="/courses" class="menu-link" @click="toggleBurger">All Courses</router-link>
          </li>
          <li class="menu-link__item">
            <router-link to="/pricing" class="menu-link" @click="toggleBurger">Pricing</router-link>
          </li>
          <li class="menu-link__item">
            <router-link to="/blog" class="menu-link" @click="toggleBurger">Blog</router-link>
          </li>
          <li class="menu-link__item">
            <router-link to="/" class="button" @click="toggleBurger">Sign in</router-link>
          </li>
          <li class="menu-link__item">
            <router-link to="/" class="button" @click="toggleBurger">Free Trial</router-link>
          </li>
        </ul>
        <ul class="menu-buttons">
          <li>
            <router-link to="/" class="button">Sign in</router-link>
          </li>
          <li>
            <router-link to="/" class="button">Free Trial</router-link>
          </li>
        </ul>
        <div class="burger-icon" :class="{ open: isOpen }" @click="toggleBurger">
          <span></span>
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
    </div>
  </header>
  <div class="content">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      isOpen: false,
    }
  },
  methods: {
    toggleBurger() {
      this.isOpen = !this.isOpen;
      if (this.isOpen) {
        document.body.classList.add('no-scroll');
      } else {
        document.body.classList.remove('no-scroll');
      }
    }
  },
}
</script>

<style lang="scss">
#header-section {
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  z-index: 50;
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: #E4F5EB;
    z-index: 2;
  }
  .container {
    .header {
      position: relative;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 20px;
      font-weight: 600;
      padding: 10px 0;
      .header__logo {
        position: relative;
        z-index: 2;
        color: #242323;
        font-size: 40px;
        font-weight: 700;
        .header__logo_green {
          color: #45B871;
        }
      }
      .header__menu {
        font-size: 18px;
        position: relative;
        z-index: 2;
        display: flex;
        gap: 30px;
        align-items: center;
        @media(max-width: 800px) {
          position: absolute;
          top: 75px;
          left: -110%;
          flex-direction: column;
          width: 100vw;
          height: calc(100vh - 75px);
          margin: 0 -10px;
          transition: left .5s ease;
          background: #45B871;
          padding-top: 100px;
          color: #fff;
          font-size: 20px;
          font-weight: bold;
        }
        &.open {
          left: 0;
        }
        .menu-link__item:nth-child(5),
        .menu-link__item:nth-child(6) {
          display: none;
          @media(max-width: 800px) {
            display: flex;
          }
        }
      }
      .menu-buttons {
        position: relative;
        z-index: 2;
        display: flex;
        gap: 20px;
        @media(max-width: 800px) {
          display: none;
        }
        .button {
          background-color: #4CAF50;
          border: none;
          color: white;
          padding: 10px 24px;
          text-align: center;
          text-decoration: none;
          display: inline-block;
          font-size: 18px;
          border-radius: 10px;
        }
      }
      .burger-icon {
        display: none;
        width: 35px;
        height: 30px;
        position: relative;
        transform: rotate(0deg);
        transition: .5s ease-in-out;
        cursor: pointer;
        @media(max-width: 800px) {
          display: block;
          position: relative;
          z-index: 2;
        }
        & span {
          display: block;
          position: absolute;
          height: 3px;
          width: 100%;
          background: #000;
          border-radius: 5px;
          opacity: 1;
          left: 0;
          transform: rotate(0deg);
          transition: .25s ease-in-out;
          &:nth-child(1) {
            top: 0px;
          }
          &:nth-child(2),
          &:nth-child(3) {
            top: 10px;
          }
          &:nth-child(4) {
            top: 20px;
          }
        }
        &.open span:nth-child(1) {
          top: 18px;
          width: 0%;
          left: 50%;
        }
        &.open span:nth-child(2) {
          transform: rotate(45deg);
        }
        &.open span:nth-child(3) {
          transform: rotate(-45deg);
        }
        &.open span:nth-child(4) {
          top: 18px;
          width: 0%;
          left: 50%;
        }
      }
    }
  }
}
</style>