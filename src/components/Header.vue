<template>
  <header class="header">
    <div class="container">
      <div class="inner">
        <a class="link" href="#">
          <img class="logo" src="../../public/img/logo-top.svg" alt="Логотип" />
        </a>
        <button class="btn">Clone now</button>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
@import "../assets/styles/vars";
.header {
  .inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    padding: 32px 0;
    @media (max-width: 1000px) {
      justify-content: center;
      gap: 20px;
    }
  }
  .btn {
    @extend %btn-r;
    @extend %btn;
    width: 171px;
    height: 61px;
    @media (max-width: 1000px) {
      width: 120px;
      height: 41px;
    }
  }
}
</style>