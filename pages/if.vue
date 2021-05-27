<template>
  <div class="memberList">
    <h2>{{title}}</h2>
    <div :key="member.id" v-for="member in members" :class="heightColor(member.height)">
      {{member.name}} / {{member.position}} #{{member.id}}
      身長{{member.height}}
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "メンバーリスト",
      members: [
        { name: "中西", position: "ガード", id: 1, height: 163 },
        { name: "佐々木", position: "フォワード", id: 2, height: 173 },
        { name: "渡辺", position: "センター", id: 3, height: 180 },
        { name: "城所", position: "パワーフォワード", id: 4, height: 176 },
        { name: "荒瀬", position: "シューティングガード", id: 5, height: 168 }
      ]
    };
  },
  methods: {
    heightColor(height) {
      if (height < 170) {
        return "blue";
      }
      if (height < 180) {
        return "green";
      }
      return "red";
    }
  }
};
</script>

<style>
.memberList {
  color: wheat;
}
.blue {
  background: blue;
}
.green {
  background: green;
}
.red {
  background: red;
}
</style>