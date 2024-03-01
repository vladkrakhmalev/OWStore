<template>
  <header class="header">
    <div class="container header__container">
      <div
        class="menu__btn"
        :class="{'_active': isOpenMenu}"
        @click="toggleOpenMenu"
      >
        <div class="menu__btn-line _1"></div>
        <div class="menu__btn-line _2"></div>
        <div class="menu__btn-line _3"></div>
      </div>
      <a href="/" class="header__logo">
        <img src="../img/logo.svg" alt="" class="header__logo-img">
      </a>
      <nav class="menu" :class="{'_open': isOpenMenu}">
        <a href="/men" class="menu__link">Мужчины</a>
        <a href="/women" class="menu__link">Женщины</a>
        <a href="/sale" class="menu__link _red">Sale</a>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isOpenMenu: false
    }
  },
  methods: {
    toggleOpenMenu() {
      this.isOpenMenu = !this.isOpenMenu
    }
  }
}
</script>

<style>
  .header {
    border-bottom: 1px solid #CCCCCC;
  }

  .header__container {
    display: grid;
    grid-template-columns: auto 1fr;
    align-items: center;
  }

  .header__logo {
    margin: 22px 40px 22px 0;
    display: block;
  }

  .header__logo-img {
    display: block;
    width: 142px;
  }

  .menu {
    display: flex;
    list-style: none;
  }

  .menu__btn {
    display: none;
  }

  .menu__link {
    padding: 27px 33px;
    border-right: 1px solid #CCCCCC;
    text-decoration: none;
    font-size: 16px;
    font-weight: bold;
    color: #38383B;
    position: relative;
  }

  .menu__link._red {
    color: #CA331E;
  }

  .menu__link:first-child {
    border-left: 1px solid #CCCCCC;
  }

  .menu__link::after {
    content: '';
    display: block;
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 0px;
    background-color: #FFC72C;
    transition: .2s;
    opacity: 0;
  }

  .menu__link:hover::after {
    opacity: 1;
    height: 3px;
  }

  @media (max-width: 1024px) {

    .header {
      background-color: #fff;
      padding: 22px 0;
      position: relative;
    }

    .header__container {
      grid-template-columns: 1fr 2fr 1fr;
      gap: 12px;
    }

    .header__logo {
      margin: 0 auto;
    }

    .menu__btn {
      display: grid;
      cursor: pointer;
      gap: 3px;
      justify-items: center;
      align-items: center;
      width: max-content;
      margin: 0 10px;
    }

    .menu__btn-line {
      height: 2px;
      width: 16px;
      background-color: #38383B;
      border-radius: 5px;
      transition: .2s;
    }

    .menu__btn._active .menu__btn-line._1 {
      transform: rotate(45deg) translate(3px, 4px);
    }

    .menu__btn._active .menu__btn-line._2 {
      width: 0;
    }

    .menu__btn._active .menu__btn-line._3 {
      transform: rotate(-45deg)translate(3px, -4px);;
    }

    .menu {
      position: absolute;
      z-index: -1;
      opacity: 0;
      top: calc(100% + 1px);
      left: 0;
      width: 100%;
      background-color: #fff;
      flex-direction: column;
      align-items: center;
      box-shadow: 0 50px 50px 0 #00000022;
      transition: .2s;
    }

    .menu._open {
      z-index: 100;
      opacity: 1;
    }

    .menu__link {
      border: none !important;
    }
  }

  @media (max-width: 768px) {
    .header {
      padding: 15px 0;
    }
  }
</style>
