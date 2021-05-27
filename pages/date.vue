<template>
  <div class="wrap">
    <p class="txt">来月1日まで</p>
    <p class="num">{{ nowTime }}</p>
    <button class="btn" v-on:click="time">COUNT</button>
    <nuxt-link to="/top" class="mod-btn">TOP</nuxt-link>
  </div>
</template>

<style>
.wrap {
    margin: 100px 0;
}

.txt {
    text-align: center;
    font-size: 24px;
    margin-bottom: 10px;
}

.num {
  font-size: 32px;
  text-align: center;
}

.btn {
  border: 2px solid black;
  font-size: 24px;
  text-align: center;
  background-color: inherit;
  display: block;
  text-align: center;
  margin: 20px auto 0;
  padding: 10px 20px;
}

.year {
  opacity: 0;
}

.newyear {
  opacity: 1;
}

* {
  outline: none;
}
</style>

<script>
export default {
  data() {
    return {
      nowTime: "残り時間",
      show: false,
    };
  },
  methods: {
    time: function () {
      let current = new Date();
      let currentDate = current.getDate();
      let currentHours = current.getHours();
      let currentMinutes = current.getMinutes();
      let currentSeconds = current.getSeconds();
      let countDate = 31 - currentDate;
      let countHours = 23 - currentHours;
      let countMinutes = 59 - currentMinutes;
      let countSeconds = 60 - currentSeconds;

      setTimeout(() => {
        this.time();
      }, 10);

      let sumTime =
        countDate +
        "日" +
        countHours +
        "時間" +
        countMinutes +
        "分" +
        countSeconds +
        "秒";

      return (this.nowTime = sumTime);
    },
  },
};
</script>

