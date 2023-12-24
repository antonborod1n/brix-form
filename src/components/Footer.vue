<template>
  <footer class="footer">
    <div class="container">
      <div class="inner">
        <div class="item">
          <a class="link" href="#">
            <img
              class="logo"
              src="../../public/img/logo-bottom.svg"
              alt="Логотип"
            />
          </a>
          <p class="copy">
            Copyright © 2021 BRIX Templates | All Rights Reserved
          </p>
        </div>
        <div class="item">
          <label class="label">
            <input class="input" type="email" placeholder="Enter your email" />
            <button class="btn">Subscribe</button>
          </label>
        </div>
      </div>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
@import "../assets/styles/vars";
.footer {
  padding: 56px 0 61px;
  border-top: 1px solid $light-gray;
  @media (max-width: 1000px) {
    padding: 30px 0;
  }
  .inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    @media (max-width: 1000px) {
      justify-content: center;
      flex-wrap: wrap;
      gap: 30px;
    }
  }
  .item {
    @media (max-width: 600px) {
      width: 100%;
    }
  }
  .logo {
    @media (max-width: 1000px) {
      margin: 0 auto;
    }
  }
  .copy {
    @extend %dms-400;
    color: $grey;
    font-size: 18px;
    line-height: 30px;
    padding-top: 17px;
    @media (max-width: 1000px) {
      font-size: 16px;
      line-height: 26px;
    }
    @media (max-width: 600px) {
      text-align: center;
    }
  }
  .label {
    position: relative;
  }
  .input {
    @extend %dms-400;
    padding: 26px 31px;
    width: 507px;
    height: 73px;
    color: $grey;
    font-size: 18px;
    line-height: 20px;
    border-radius: 60px;
    border: 1px solid $white2;
    background-color: $white;
    box-shadow: 0px 8px 25px 0px rgba(13, 10, 44, 0.06);
    @media (max-width: 1000px) {
      flex-wrap: wrap;
      padding: 20px;
      height: 53px;
      font-size: 16px;
      line-height: 26px;
    }
    @media (max-width: 600px) {
      width: 100%;
    }
  }
  .btn {
    position: absolute;
    top: -13px;
    right: 19px;
    @extend %btn-r;
    @extend %btn;
    @extend %dms-500;
    padding: 14px 26px 17px 26px;
    border-radius: 56px;
    font-size: 16px;
    line-height: 18px;
    width: 129px;
    height: 49px;
    outline: none;
    @media (max-width: 1000px) {
      height: 43px;
      top: -11px;
      right: 5px;
    }
  }
}
</style>