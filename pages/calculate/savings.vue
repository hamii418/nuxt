<template>
  <div class="main">
    <section class="section-contents section-contents--yellow">
      <div class="container">
        <h1 class="section-ttl"><span class="section-ttl__inner">1ヶ月の生活費</span></h1>
        <div class="cal-block">
          <div class="cal-block__container">
            <table class="cal-block__table">
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >住居費<span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_house.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price1"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >食費<span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_food.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price2"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >光熱費<span class="cal-block__label-s"
                      >(電気代、ガス代、水道代)</span
                    ><span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_light.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price3"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >通信費<span class="cal-block__label-s"
                      >(携帯代、wifi代)</span
                    ><span class="cal-block__label-icon"
                      ><img
                        src="~/assets/image/icon_smartphone.svg"
                        alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price4"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >保険代<span class="cal-block__label-icon"
                      ><img
                        src="~/assets/image/icon_document.svg"
                        alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price5"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >交通費<span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_train.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price6"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >日用品<span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_shampoo.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price7"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >服・美容代<span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_cloth.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price8"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >交際費<span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_beer.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price9"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >趣味<span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_movie.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price10"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
              <tr class="cal-block__row">
                <td class="cal-block__left">
                  <label class="cal-block__label"
                    >その他<span class="cal-block__label-icon"
                      ><img src="~/assets/image/icon_money.svg" alt="" /></span
                  ></label>
                </td>
                <td class="cal-block__right">
                  <input
                    v-model.number="price11"
                    class="cal-block__input"
                  /><span class="cal-block__yen">円</span>
                </td>
              </tr>
            </table>
            <div class="cal-block__total">
              <p class="cal-block__total-txt">1ヶ月の合計金額</p>
              <div class="cal-block__total-num">
                <span class="cal-block__sum">{{ sum | numberWithDelimiter}}</span
                ><span class="cal-block__yen">円</span>
              </div>
            </div>
            <div class="cal-block__year">
              <div class="cal-block__year-block">
                <label class="cal-block__year-lable">年収</label>
                <input v-model.number="income" class="cal-block__input" /><span
                  class="cal-block__yen"
                  >円</span
                >
              </div>
              <div class="cal-block__year-block">
                <p class="cal-block__year-txt">年間支出</p>
                <span class="cal-block__year-num">{{ spend | numberWithDelimiter}}</span
                ><span class="cal-block__yen">円</span>
              </div>
              <div class="cal-block__year-block">
                <p class="cal-block__year-txt">年間残額</p>
                <span class="cal-block__year-num">{{ remain | numberWithDelimiter}}</span
                ><span class="cal-block__yen">円</span>
              </div>
            </div>
          </div>
          <nuxt-link to="/top" class="mod-btn">TOP</nuxt-link>
        </div>
      </div>
    </section>
  </div>
</template>

<style lang="scss">
input,
button,
textarea,
select {
  margin: 0;
  padding: 0;
  outline: none;
  border: none;
  box-shadow: none;
  border-radius: 0;
  background: none;
  text-indent: 0.01px;
  text-overflow: "";
  -webkit-appearance: none;
  appearance: none;
}

button {
  cursor: pointer;
}

@keyframes ttl-anime {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.site-ttl {
  text-align: center;
}

.anime {
  opacity: 0;
  animation: 3s linear forwards ttl-anime;
  font-size: 50px;
}

@media screen and (max-width: 750px) {
    .anime {
        font-size: 7.5vw;
    }
}

.anime--1 {
  animation-delay: 0.1s;
}

.anime--2 {
  animation-delay: 0.2s;
}

.anime--3 {
  animation-delay: 0.3s;
}

.anime--4 {
  animation-delay: 0.4s;
}

.anime--5 {
  animation-delay: 0.5s;
}

.anime--6 {
  animation-delay: 0.6s;
}
.anime--7 {
  animation-delay: 0.7s;
}

.anime--8 {
  animation-delay: 0.8s;
}

.main {
  color: #333;
}

.section-contents {
  padding: 50px 0;
}

@media screen and (max-width: 750px) {
    .section-contents {
        padding: 7.5vw 0;    
    }
}

.section-ttl {
  font-size: 36px;
  text-align: center !important;
  font-weight: bold;
  margin-bottom: 50px;
}

@media screen and (max-width: 750px) {
    .section-ttl {
        font-size: 5.4vw;
        margin-bottom: 7.5vw;   
    }
}

.section-ttl__inner {
    position: relative;
}

.section-ttl__inner:after {
    content: "";
    position: absolute;
    left: 0;
    bottom: 0px;
    z-index: -1;
    width: 0;
    height: 10px;
    background: gold;
    animation: 0.5s linear forwards border-anime;
}

@media screen and (max-width: 750px) {
    .section-ttl__inner:after {
        height: 1.5vw;
    }
}

.container {
  width: 800px;
  margin: 0 auto;
}

@media screen and (max-width: 750px) {
    .container {
        width: 100%;
        padding: 0 3vw;
        box-sizing: border-box; 
    }   
}

.cal-block__table {
  width: 600px;
  margin: 0 auto;
}

@media screen and (max-width: 750px) {
    .cal-block__table {
        width: 100%;
    }   
}

.cal-block__row {
  display: flex;
  align-items: center;
  padding-bottom: 10px;
}

@media screen and (max-width: 750px) {
    .cal-block__row {
        padding: 1.5vw;  
    }
}

.cal-block__left {
  width: 55%;
}

.cal-block__right {
  width: 45%;
}

.cal-block__label {
  display: flex;
  align-items: center;
  font-size: 20px;
}

@media screen and (max-width: 750px) {
    .cal-block__label {
        font-size: 3vw;
    }
}

.cal-block__label-s {
  font-size: 0.8em;
}

.cal-block__label-icon {
  display: inline-block;
  width: 20px;
  margin-left: 0.2em;
}

@media screen and (max-width: 750px) {
    .cal-block__label-icon {
        width: 3vw;
    }
}

.cal-block__label-icon img {
  width: 100%;
}

.cal-block__input {
  border: 1px solid #ccc;
  width: 200px;
  height: 45px;
  border-radius: 5px;
  font-size: 20px;
  padding: 0 0.5em;
  text-align: right;
}

@media screen and (max-width: 750px) {
    .cal-block__input {
        width: 30vw;
        height: 6.75vw;
    }
}

.cal-block__yen {
  margin-left: 1em;
}

.cal-block__total {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.cal-block__total-num {
  position: relative;
  display: flex;
  margin-left: 0.5em;
  padding-left: 0.5em;
  align-items: baseline;
  border-bottom: 4px solid gold;
}

@media screen and (max-width: 750px) {
   .cal-block__total-num {
       border-bottom: 1vw solid gold;
   } 
}

.cal-block__sum {
  font-weight: bold;
  font-size: 40px;
}

@media screen and (max-width: 750px) {
    .cal-block__sum {
        font-size: 6vw;
    }
}

.cal-block__year-block {
    display: flex;
    align-items: baseline;
}

.cal-block__year-lable {
    margin-right: 1em;
}

.cal-block__year-num {
    font-size: 36px;
    margin-left: 1em;
    text-align: right;
}

@media screen and (max-width: 750px) {
    .cal-block__year-num {
        font-size: 5.4vw;
    }
}

</style>
<script>
export default {
  data() {
    return {
      price1: 0,
      price2: 0,
      price3: 0,
      price4: 0,
      price5: 0,
      price6: 0,
      price7: 0,
      price8: 0,
      price9: 0,
      price10: 0,
      price11: 0,
      income: 0
    };
  },
  computed: {
    sum() {
      return (
        this.price1 + this.price2 + this.price3 + this.price4 + this.price5 + this.price6 + this.price6 + this.price7 + this.price8 + this.price9 + this.price10 
      );
    },
    spend() {
      return this.sum * 12;
    },
    remain() {
      return this.income - this.spend;
    }
  },
   filters: {
    numberWithDelimiter(value) {
      if(!value) return '0'
      return value.toString().replace(/(\d)(?=(\d{3})+$)/g, '$1, ')
    }
  }
};
</script>
