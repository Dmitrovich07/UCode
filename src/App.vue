<template>
  <header id="header-section">
    <div class="container">
      <div class="header">
        <h1 class="header__logo">
          <span class="header__logo_green">U</span>-Coda
        </h1>
        <ul class="menu-list" :class="{ open: isOpen }">
          <li class="menu-link"><router-link to="/">Home</router-link></li>
          <li class="menu-link"><router-link to="/courses" class="nav-main-btn">All Courses</router-link></li>
          <li class="menu-link"><router-link to="/pricing">Pricing</router-link></li>
          <li class="menu-link"><router-link to="/blog">Blog</router-link></li>
        </ul>
        <ul class="actions-list">
          <li class="actions-link">
            <router-link to="/" class="btn-login">Sign in</router-link>
            <!-- <a href="#" class="header-action__link header-action__log">Sign in</a> -->
          </li>
          <li class="actions-link">
            <router-link to="/" class="btn-primary">Free Trial</router-link>
            <!-- <a href="#" class="header-action__link btn-primary">Free Trial</a> -->
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
      height: 100px;
      padding: 40px 0 0 0;
      @media(max-width: 780px) {
        padding: 0;
        height: 60px;

      }
      .header__logo {
        position: relative;
        z-index: 2;
        color: #242323;
        font-size: 40px;
        font-size: clamp(24px, 3vw, 30px);
        font-weight: 700;
        .header__logo_green {
          color: #45B871;
        }
      }
      .menu-list {
        position: relative;
        z-index: 2;
        display: flex;
        justify-content: center;
        gap: 20px;
        background-color: #E4F5EB;          
        transition: top .5s ease;
        @media(max-width: 780px) {
          position: fixed;
          z-index: 1;
          top: 0;
          left: 0;
          width: 100%;
        }
        @media(max-width: 400px) {
          top: -100%;
          align-items: center;
          justify-content: start;
          flex-direction: column;
          padding: 80px 0 0 0;
        }
        &.open {
          top: 60px;
          @media(max-width: 400px) {
            height: 100%;
          }
        }
      }
      .actions-list {
        position: relative;
        z-index: 2;
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 20px;
        @media(max-width: 450px) {
          display: none;
        }
        .actions-link {
          .btn-primary {
            display: block;
            width: 135px;
            padding: 10px 0;
            @media(max-width: 780px) {
              width: 120px;
              padding: 5px 0;
            }
          }
        }
        }
      .burger-icon {
        display: none;
        width: 40px;
        height: 35px;
        position: relative;
        transform: rotate(0deg);
        transition: .5s ease-in-out;
        cursor: pointer;
        @media(max-width: 780px) {
          display: block;
          position: relative;
          z-index: 2;
        }
        & span {
          display: block;
          position: absolute;
          height: 5px;
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
            top: 12px;
          }
          &:nth-child(4) {
            top: 24px;
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
// $top-padding: 40px;
// $height-header: 60px;
// // E4F5EB бекграунд
// #header-section {
//   position: relative;
//   // z-index: -2;
//   background-color: #E4F5EB;
//   // padding: $top-padding 0 0;
//   // background-color: #E4F5EB;
//   .container {
//     .header {
//       background-color: #E4F5EB;
//       padding: 40px 0 0 0;
//       // height: $height-header;
//       display: flex;
//       // justify-content: space-between;
//       align-items: center;
//       height: 80px;
//       color: #575859;
//       font-size: 20px;
//       font-weight: 600;
//       .header__logo {
//         margin-right: 100px;
//         color: #242323;
//         font-size: 30px;
//         font-weight: 700;
//         .header__logo_green {
//           color: #45B871;
//         }
//       }
//       .menu {
//         position: absolute;
//         // z-index: -3;
//         top: 0;
//         left: 0;
//         background-color: aqua;
//         padding: 0 50px;
//         .menu-list {
//           display: flex;
//           justify-content: center;
//           align-items: center;
//           gap: 20px;
//         }
//       }
//       .nav-main {
//         transition: top 0.5s ease;
//         @media(max-width: 950px) {
//           position: absolute;
//           width: 100%;
//           top: 0;
//           left: 0;
//           background-color: #E4F5EB;
//           // transform: translate(-100%, 100px);
//         }
//         @media(max-width: 420px) {
//           height: calc(100% - ($height-header + $top-padding));
//         }
//         &.open {
//           top: calc($height-header + $top-padding);
//           // transform: translate(0, 100px);

//         }
//         .nav-main__list {
//           display: flex;
//           justify-content: center;
//           align-items: center;
//           gap: 60px;
//           @media(max-width: 950px) {
//             gap: 80px;
//           }
//           @media(max-width: 600px) {
//             gap: 30px;
//           }
//           @media(max-width: 420px) {
//             flex-direction: column;
//           }
//           .nav-main__item {
//             font-size: 20px;
//             font-weight: 600;
//             transition: all .4s ease;
//             color: grey;
//             &:hover {
//               color: #45B871;
//               cursor: pointer;
//             }
//             .router-link-active {
//               color: #000;
//               font-weight: 700;
//               cursor: default;
//                 &:hover {
//                 cursor: default;
//               }
//             }
//             .nav-main-btn {
//               position: relative;
//               padding-right: 20px;
//               &::after {
//                 content: '';
//                 position: absolute;
//                 top: 60%;
//                 right: 0;
//                 width: 10px;
//                 height: 10px;
//                 background: url('./assets/arrow.svg') 50%/100% no-repeat;
//                 transform: translateY(-50%);
//                 transition: .4s;
//               }
//               &:hover::after {
//                 background: url('./assets/arrow_green.svg') 50%/100% no-repeat;
//               }
//             }
//           }
//         }
//         .header-action-burger {
//           margin-top: 50px;
//           width: 100%;
//           display: none;
//           gap: 20px;
//           align-items: center;
//           @media(max-width: 420px) {
//             display: flex;
//             flex-direction: column;
//           }
//           .header-action__item {
//             .header-action__link {
//               &.btn-primary {
//                 display: block;
//                 width: 135px;
//               }
//             } 
//           }
//         }
//       }
//       .header-action {
//         display: flex;
//         justify-content: space-between;
//         align-items: center;
//         gap: 40px;
//         @media(max-width: 600px) {
//           gap: 20px;
//         }
//         @media(max-width: 420px) {
//           display: none;
//         }
//         .header-action__item {
//           .header-action__link {
//             &.btn-primary {
//               display: block;
//               width: 135px;
//             }
//           } 
//         }
//       }
//       .burger-icon {
//         display: none;
//         width: 40px;
//         height: 35px;
//         position: relative;
//         transform: rotate(0deg);
//         transition: .5s ease-in-out;
//         cursor: pointer;
//         @media(max-width: 950px) {
//           display: block;
//         }
//         & span {
//           display: block;
//           position: absolute;
//           height: 5px;
//           width: 100%;
//           background: #000;
//           border-radius: 5px;
//           opacity: 1;
//           left: 0;
//           transform: rotate(0deg);
//           transition: .25s ease-in-out;
//           &:nth-child(1) {
//             top: 0px;
//           }
//           &:nth-child(2),
//           &:nth-child(3) {
//             top: 12px;
//           }
//           &:nth-child(4) {
//             top: 24px;
//           }
//         }
//         &.open span:nth-child(1) {
//           top: 18px;
//           width: 0%;
//           left: 50%;
//         }
//         &.open span:nth-child(2) {
//           transform: rotate(45deg);
//         }
//         &.open span:nth-child(3) {
//           transform: rotate(-45deg);
//         }
//         &.open span:nth-child(4) {
//           top: 18px;
//           width: 0%;
//           left: 50%;
//         }
//       }
//     }
//   }
// }
</style>