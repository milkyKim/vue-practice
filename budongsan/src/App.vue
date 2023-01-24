<template>
  <h2>민지부동산</h2>

  <div class="black-bg" v-if="isOpenModal == true">
    <div class="white-bg">
      <h4 style="display: inline">상세 페이지</h4>
      <button v-on:click="openModal(false)">닫기</button>
      <p>{{ products[0].content }}</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, idx) in menus" :key="idx">{{ menu }}</a>
  </div>

  <div v-for="(product, idx) in products" :key="idx">
    <img :src="product.image" class="room-img" />
    <h4 v-on:click="openModal(true)">{{ product.title }}</h4>
    <p>{{ product.price }} 만원</p>
    <button v-on:click="increase(idx)">허위매물신고</button>
    <span>신고 수: {{ product.reportCnt }}</span>
  </div>
</template>

<script>
import postList from "./data/post.js";

export default {
  name: "App",
  data() {
    return {
      menus: ["Home", "Shop", "About"],
      products: postList,
      isOpenModal: false,
    };
  },
  methods: {
    increase(idx) {
      return this.products[idx].reportCnt++;
    },
    openModal(isOpenModal) {
      return (this.isOpenModal = isOpenModal);
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.white-bg button {
  position: fixed;
  right: 30px;
}
</style>
