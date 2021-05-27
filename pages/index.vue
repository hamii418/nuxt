<template>
  <div id="wrap" class="wrap">
    <div>
      <div class="header">
        <div class="header-container">
          <div class="header-logo">
            <img src="~/assets/image/img_header-logo.png" alt="" />
          </div>
          <div
            class="header-btn pc-hide"
            @click="navOpen"
            :class="{ active: headerBtnActive }"
          ></div>
          <transition name="header-nav">
            <div class="header-nav" v-show="headerNavActive">
              <transition name="header-nav-list">
                <ul class="header-nav__list" v-show="headerNavListActive">
                  <li class="header-nav__list-item">
                    <a href="" class="header-nav__list-link">リンク</a>
                  </li>
                  <li class="header-nav__list-item">
                    <a href="" class="header-nav__list-link">リンク</a>
                  </li>
                  <li class="header-nav__list-item">
                    <a href="" class="header-nav__list-link">リンク</a>
                  </li>
                  <li class="header-nav__list-item">
                    <a href="" class="header-nav__list-link">リンク</a>
                  </li>
                  <li class="header-nav__list-item">
                    <a href="" class="header-nav__list-link">リンク</a>
                  </li>
                  <li class="header-nav__list-item">
                    <a href="" class="header-nav__list-link">リンク</a>
                  </li>
                </ul>
              </transition>
            </div>
          </transition>
        </div>
      </div>

      <div class="contents">
        <client-only>
          <swiper :options="swiperOption">
            <swiper-slide
              ><img src="~/assets/image/img_slide_01.jpg" alt=""
            /></swiper-slide>
            <swiper-slide
              ><img src="~/assets/image/img_slide_02.jpg" alt=""
            /></swiper-slide>
            <swiper-slide
              ><img src="~/assets/image/img_slide_03.jpg" alt=""
            /></swiper-slide>
          </swiper>
        </client-only>
      </div>

        <section class="mod-block">
          <div class="mod-block__container">
          <h2 class="mod-ttl">このサイトについて</h2>
          <p class="mod-txt">Nuxt.jsのSSRで実装しています。</p>
          <h3 class="mod-sub-ttl">主な仕様、大変だったこと</h3>
          <ul class="mod-list">
            <li class="mod-list__item">GoogleFontを使用</li>
            <li class="mod-list__item">scssを導入して、開発。バージョンが異なりエラーが出たので、その対応が大変でした。</li>
            <li class="mod-list__item">ハンバーガーメニューは、@click、transition、v-show、class付与を使用し自作</li>
            <li class="mod-list__item">スライダーは、swiperプラグインを使用し実装。SSRでエラーが出たので、その対応が大変でした。</li>
            <li class="mod-list__item">ページトップボタンは、スクロールでfadeinを実装するのに、スクロール値の計算をするのに、window is not definedになったので大変でした。</li>
            <li class="mod-list__item">ページトップボタンに、vue-scrollto.jsのプラグインを使用しています。</li>
          </ul>
          </div>          　　
        </section>

        <section class="mod-block">
          <div class="mod-block__container">
          <h2 class="mod-ttl">1ヶ月の生活費</h2>
          <p class="mod-txt">住居費、食費など、1ヶ月にかかる費用を入力して合計値を算出致します。年収を入れることで、年間残額も計算できます。<br>computedを使用して、計算しています。</p>
          <nuxt-link to="/calculate/savings" class="mod-btn">ページへ</nuxt-link>
          </div>          　　
        </section>

        <section class="mod-block">
          <div class="mod-block__container">
          <h2 class="mod-ttl">カウントダウン</h2>
          <p class="mod-txt">来月1日までのカウントダウンを作成致しました。countボタンを押すとカウントダウンが始まります。<br>getDate等を使用して、計算しています。</p>
          <nuxt-link to="/date" class="mod-btn">ページへ</nuxt-link>
          </div>          　　
        </section>

        <div class="fix-btn" v-show="visible"><nuxt-link v-scroll-to="'#wrap'" to class="page-top"><span class="page-top__arrow"></span></nuxt-link></div>

    </div>
  </div>
</template>

<script>
import { getWindow, getDocument } from "ssr-window";

const window = getWindow();
const document = getDocument();

window.addEventListener("resize", () => {});

const div = document.querySelectorAll("div");

export default {
  data() {
    return {
      swiperOption: {
        autoplay: {
          delay: 2500,
          disableOnInteraction: false,
        },
        slidesPerView: 1,
        loop: true,
      },
      scrollY: 0,
      count: 0,
      headerBtnActive: false,
      headerNavActive: false,
      headerNavListActive: false,
      visible: false
    };
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      if (!this.visible) {
        var top = this.$el.getBoundingClientRect().top;
        this.visible = top < window.innerHeight + 200;
      }
    },
    navOpen() {
      (this.headerBtnActive = !this.headerBtnActive),
        (this.headerNavActive = !this.headerNavActive),
        (this.headerNavListActive = !this.headerNavListActive);
    },
  },
};
</script>

<style lang="scss">
.contents {
  margin-top: 80px;

  @media screen and (max-width: 750px) {
    margin-top: 60px;
  }
}

.header {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 2000;
  width: 100%;
  height: 80px;
  background: #fff;

  @media screen and (max-width: 750px) {
    height: 60px;
  }
}

.header-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
  padding: 0 20px;
}

.header-nav {
  @media screen and (min-width: 751px) {
    display: block !important;
  }

  @media screen and (max-width: 750px) {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
    height: 100vh;
    width: 100%;
    background: #fff;
  }

  &__list {

    @media screen and (min-width: 751px) {
      display: flex !important;
    }

    @media screen and (max-width: 750px) {
      display: block;
      margin-top: 15vw;
    }
  }

  &__list-item {
    margin-right: 20px;

    @media screen and (max-width: 750px) {
      margin-right: 0;
      margin-bottom: 8vw;
    }

    &:last-of-type {
      margin-right: 0;
    }
  }

  &__list-link {
    position: relative;
    display: block;
    text-align: center;
    font-size: 16px;

    @media screen and (max-width: 750px) {
      font-size: 4.8vw;
    }

    &:after {
      content: "";
      position: absolute;
      left: 0;
      bottom: -8px;
      width: 0;
      height: 3px;
      background: deeppink;
      transition: 0.3s;

      @media screen and (max-width: 750px) {
        content: none;
      }
    }

    &:hover:after {
      width: 100%;
    }
  }
  &-enter,
  &-leave-to {
    height: 0;
  }
  &-enter-to,
  &-leave {
    height: 100vh;
  }
  &-enter-active,
  &-leave-active {
    transition: 0.3s;
  }
}

.header-nav-list {
  &-enter,
  &-leave-to {
    opacity: 0;
  }
  &-enter-to,
  &-leave {
    opacity: 1;
  }
  &-enter-active {
    transition: 0.5s;
  }
  &-leave-active {
    transition: 0.1s;
  }
}

.header-btn {
  position: relative;
  z-index: 1000;
  width: 30px;
  height: 30px;
  margin-left: auto;
  background-image: url(~@/assets/image/icon_menu.svg);
  transition: 0.3s;

  &.active {
    background-image: url(~@/assets/image/icon_close.svg);
    transition: 0.3s;
  }
}

.mod-block {
  padding: 50px 0;

  @media screen and (max-width: 750px) {
    padding: 10vw 0;
  }

  &:nth-of-type(2n) {
    background-color: rgba(pink,0.2);
  }

  &__container {
    max-width: 800px;
    margin: 0 auto;
    padding: 0 20px;

    @media screen and (max-width: 750px) {
      padding: 0 3vw;
    }
  }
}

.mod-ttl {
  font-size: 32px;
  text-align: center;
  margin-bottom: 50px;

  @media screen and (max-width: 750px) {
    font-size: 6.4vw;
    margin-bottom: 5vw;
  }
}

.mod-txt {
  font-size: 16px;
  line-height: 1.8;

  @media screen and (max-width: 750px) {
    font-size: 3.2vw;
  }
}

.mod-btn {
  width: 250px;
  height: 60px;
  margin: 50px auto 0;
  background-color: deeppink;
  color: #fff;
  border: 2px solid deeppink;
  font-weight: bold;
  border-radius: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: 0.3s;

  @media screen and (max-width: 750px) {
    margin-top: 5vw;
    width: 50vw;
    height: 12vw;
  }

  &:hover {
    background-color: #fff;
    color: deeppink;
  }
}

.mod-sub-ttl {
  font-size: 20px;
  margin-top: 30px;
  margin-bottom: 15px;

  @media screen and (max-width: 750px) {
    font-size: 3vw;
  }

  &:before {
    content: "◎";
    color: deeppink;
    margin-right: 0.2em;
  }
}

.mod-list {
  &__item {
  margin-bottom: 10px;
  line-height: 1.5;
  display: flex;

  @media screen and (max-width: 750px) {
    margin-bottom: 1.5vw;
  }

    &:before {
      content: "・";
      color: deeppink;
    }
  }
}

.fix-btn {
  position: fixed;
  bottom: 0;
  right: 0;
}

.page-top {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: block;
  background-color: deeppink;
  transition: 0.3;

  &:hover {
    opacity: 0.8;
  }

  &__arrow {
    display: block;

    &:after {
      content: "";
      position: absolute;
      top: 55%;
      left: 50%;
      display: block;
      width: 20px;
      height: 20px;
      border-top: 3px solid #fff;
      border-right: 3px solid #fff;
      transform: translate(-50%,-50%) rotate(-45deg);
    }
  }
}

</style>

