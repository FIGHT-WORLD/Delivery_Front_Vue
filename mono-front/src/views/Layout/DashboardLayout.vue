<template>
  <div class="wrapper">
    <notifications></notifications>
    <side-bar>
      <template slot="links">
        <!-- <sidebar-item
          :link="{
            name: '주문 정보',
            path: '/dashboard',
            icon: 'ni ni-cart',
          }"
        >
        </sidebar-item> -->

        <sidebar-item
          :link="{
            name: '사용자',
            path: '/user',
            icon: 'ni ni-single-02 text-yellow',
          }"
        >
        </sidebar-item>

        <sidebar-item
          :link="{
            name: '문의 게시판',
            path: '/report',
            icon: 'ni ni-bullet-list-67 text-red',
          }"
        >
        </sidebar-item>

        <sidebar-item
          :link="{
            name: '스토어',
            path: '/store',
            icon: 'ni ni-shop text-blue',
          }"
        >
        </sidebar-item>

           <sidebar-item
          :link="{
            name: 'Ai',
            path: '/ai',
            icon: 'ni ni-planet text-blue',
          }"
        >
        </sidebar-item>

        <!-- <sidebar-item
            :link="{
              name: 'Icons',
              path: '/icons',
              icon: 'ni ni-planet text-blue'
              }"
            >
        </sidebar-item> -->

        <!-- 
        <sidebar-item
              :link="{
                name: 'User Profile',
                path: '/profile',
                icon: 'ni ni-single-02 text-yellow'
                }">
        </sidebar-item> -->

        <sidebar-item
          :link="{
            name: '로그인',
            path: '/auth/login',
            icon: 'ni ni-key-25 text-info',
          }"
        >
        </sidebar-item>
        <sidebar-item
          :link="{
            name: '회원가입',
            path: '/auth/register',
            icon: 'ni ni-circle-08 text-pink',
          }"
        >
        </sidebar-item>
      </template>
    </side-bar>
    <div class="main-content">
      <dashboard-navbar :type="$route.meta.navbarType"></dashboard-navbar>

      <div @click="$sidebar.displaySidebar(false)">
        <fade-transition :duration="200" origin="center top" mode="out-in">
          <!-- your content here -->
          <router-view></router-view>
        </fade-transition>
      </div>
      <content-footer v-if="!$route.meta.hideFooter"></content-footer>
    </div>
  </div>
</template>
<script>
/* eslint-disable no-new */
import PerfectScrollbar from "perfect-scrollbar";
import "perfect-scrollbar/css/perfect-scrollbar.css";

function hasElement(className) {
  return document.getElementsByClassName(className).length > 0;
}

function initScrollbar(className) {
  if (hasElement(className)) {
    new PerfectScrollbar(`.${className}`);
  } else {
    // try to init it later in case this component is loaded async
    setTimeout(() => {
      initScrollbar(className);
    }, 100);
  }
}

import DashboardNavbar from "./DashboardNavbar.vue";
import ContentFooter from "./ContentFooter.vue";
import DashboardContent from "./Content.vue";
import { FadeTransition } from "vue2-transitions";

export default {
  components: {
    DashboardNavbar,
    ContentFooter,
    DashboardContent,
    FadeTransition,
  },
  methods: {
    initScrollbar() {
      let isWindows = navigator.platform.startsWith("Win");
      if (isWindows) {
        initScrollbar("sidenav");
      }
    },
  },
  mounted() {
    this.initScrollbar();
  },
};
</script>
<style lang="scss"></style>
