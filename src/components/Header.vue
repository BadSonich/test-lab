<template>
  <header class="header">
    <div class="container">
      <a href="/">
        <img class="header__logo" src="../assets/logo.png" alt="logo">
      </a>
      <div class="header__mob-menu" @click="toggleMenu"></div>
      <div class="header__menu submenu" :class="{active : menuActive}">
        <div class="submenu__header">
          <a href="/">
            <img src="../assets/logo-mob.svg" alt="logo">
          </a>
          <span class="submenu__close" @click="toggleMenu"></span>
        </div>
        <a href="/#how-it-works">Как это работает</a>
        <a href="/#third-block">3-й блок</a>
        <a href="/#faq">Вопросы и ответы</a>
        <a href="/#">Форма</a>
      </div>
    </div>
  </header>
</template>

<script>
  export default {
    name: 'site-header',
    data() {
      return {
        menuActive: false
      }
    },
    methods: {
      toggleMenu() {
        this.menuActive = !this.menuActive;
      }
    }
  }
</script>