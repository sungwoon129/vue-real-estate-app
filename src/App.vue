<template>

<div class="black-bg" v-if="isModalView">
  <div class="white-bg">
    <h4>상세페이지임</h4>
    <p>상세페이지 내용임</p>
    <div>
      <button @click="isModalView = false">닫기</button>
    </div>
  </div>
</div>

  <div class="menu">
    <a v-for="(menu,i) in menus" :key="i">{{ menu }}</a>
  </div>
  <div v-for="product in products" :key="product.id">
    <img :src='product.image' class="room-img">
    <h4 @click="isModalView = true" class="item-title">{{product.title}}</h4>
    <p>{{product.price}}원</p>
    <p>{{product.content}}</p>
    <button @click="increase(product, $event)" class="mr-2">허위매물 신고</button> 
  
  </div>
</template>

<script>

import data from './assets/data';

export default {
  name: 'App',
  data() {
    return {
      menus : ['Home','Shop', 'About'],
      isModalView: false,
      products:data,
    }
  },
  methods: {
    increase(product) {
      product.신고수++;
    }
  },
  components: {
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  margin : 0
}
div {
  box-sizing: border-box;
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
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.mr-2 {
  margin-right: 20px;
}
.item-title {
  cursor: pointer;
}
.item-title:hover {
  color: skyblue;
}
</style>
