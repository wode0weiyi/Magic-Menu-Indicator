<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
import { ref } from "vue";

const currentIndex = ref(1);
function activeLink(index: number) {
  currentIndex.value = index;
}

defineProps({
  indicatorColor: {
    type: String,
    default: "#26cb78",
  },
});
</script>

<template>
  <div class="tabbar">
    <ul>
      <li
        class="list"
        :class="{ active: currentIndex === 1 }"
        @click="activeLink(1)"
      >
        <a href="#">
          <span class="icon"
            ><i class="iconfont icon-icontabbarhomeup"></i
          ></span>
          <span class="text">home</span>
        </a>
      </li>
      <li
        class="list"
        :class="{ active: currentIndex === 2 }"
        @click="activeLink(2)"
      >
        <a href="#">
          <span class="icon"><i class="iconfont icon-icontabbarmyup"></i></span>
          <span class="text">mine</span>
        </a>
      </li>
      <li
        class="list"
        :class="{ active: currentIndex === 3 }"
        @click="activeLink(3)"
      >
        <a href="#">
          <span class="icon"><i class="iconfont icon-icnotification"></i></span>
          <span class="text">notice</span>
        </a>
      </li>
      <li
        class="list"
        :class="{ active: currentIndex === 4 }"
        @click="activeLink(4)"
      >
        <a href="#">
          <span class="icon"><i class="iconfont icon-tabbar-hold"></i></span>
          <span class="text">news</span>
        </a>
      </li>
      <li
        class="list"
        :class="{ active: currentIndex === 5 }"
        @click="activeLink(5)"
      >
        <a href="#">
          <span class="icon"
            ><i class="iconfont icon-tabbar-bookmark"></i
          ></span>
          <span class="text">shop</span>
        </a>
      </li>
      <div class="pointer" :style="{ background: indicatorColor }"></div>
    </ul>
  </div>
</template>
<style lang="css">
:root {
  --clr: #999999;
}
body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}
.tabbar {
  display: flex;
  background: #fff;
  position: relative;
  height: 70px;
  width: 400px;
  justify-content: center;
  align-content: center;
  border-radius: 10px;
}
.tabbar ul {
  display: flex;
  width: 350px;
  padding: 0;
}
.tabbar ul li {
  position: relative;
  list-style: none;
  width: 70px;
  height: 70px;
  z-index: 1;
}
.tabbar ul li a {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  text-align: center;
  font-weight: 500;
  background-color: transparent;
}
.tabbar ul li a .icon {
  position: relative;
  display: block;
  line-height: 75px;
  width: 70px;
  font-size: 1.5rem;
  text-align: center;
  transition: 0.5s;
  color: var(--clr);
}
.tabbar ul li.active a .icon {
  transform: translateY(-38px);
  color: #fff;
}
.tabbar ul li a .icon i {
  font-size: 25px;
}
.tabbar ul li a .text {
  position: absolute;
  color: var(--clr);
  line-height: 16px;
  font-weight: 400;
  letter-spacing: 0.05em;
  transition: 0.5s;
  transform: translateY(20px);
  opacity: 0;
}
.tabbar ul li.active a .text {
  opacity: 1;
  transform: translateY(10px);
}
.pointer {
  background: #26cb78;
  width: 70px;
  height: 70px;
  border: 6px solid var(--clr);
  border-radius: 35px;
  position: absolute;
  top: -50%;
  transition: 0.5s;
}
.pointer::after {
  content: " ";
  background: transparent;
  position: absolute;
  top: 50%;
  right: -22px;
  width: 20px;
  height: 20px;
  border-top-left-radius: 20px;
  box-shadow: 0px -10px 0 0 var(--clr);
}
.pointer::before {
  content: " ";
  background: transparent;
  position: absolute;
  top: 50%;
  left: -22px;
  width: 20px;
  height: 20px;
  border-top-right-radius: 20px;
  box-shadow: 0px -10px 0 0 var(--clr);
}
.tabbar ul li:nth-child(1).active ~ .pointer {
  transform: translateX(calc(70px * 0));
}
.tabbar ul li:nth-child(2).active ~ .pointer {
  transform: translateX(calc(70px * 1));
}
.tabbar ul li:nth-child(3).active ~ .pointer {
  transform: translateX(calc(70px * 2));
}
.tabbar ul li:nth-child(4).active ~ .pointer {
  transform: translateX(calc(70px * 3));
}
.tabbar ul li:nth-child(5).active ~ .pointer {
  transform: translateX(calc(70px * 4));
}
</style>
