<template>
  <v-toolbar flat scroll-off-screen color="white">
    <v-layout fill-height class="hearder-container">
      <a href="/" class="logo">
        <v-layout hidden-sm-and-down>
          <img src="../static/img/bojun.jpg" alt>
        </v-layout>
        <v-layout hidden-sm-and-up>
          <img src="../static/img/bojun_logo.jpg" alt>
        </v-layout>
      </a>
      <v-layout class="nav">
        <ul class="nav-main">
          <li
            v-for="(item, index) in navList"
            :key="index"
            :class="{'nav-main-active': activeNav}"
          >{{item.name}}</li>
        </ul>
        <v-layout>
          <v-flex :class="['nav-search', isActive ? 'active': '']">
            <input
              type="text"
              placeholder="搜索更新啦"
              :value="searchContent"
              @focus="isActive = !isActive"
              @blur="isActive = !isActive"
            >
            <v-icon small size="20">search</v-icon>
          </v-flex>
          <v-flex class="nav-notify">
            <v-badge overlap>
              <template v-slot:badge class="badge-change">
                <span>6</span>
              </template>
              <v-icon>notifications</v-icon>
            </v-badge>
          </v-flex>
          <v-flex>
            <span>登录</span>
            <i>dian</i>
          </v-flex>
        </v-layout>
      </v-layout>
      <!-- <v-flex align-content-center class="nav"> -->

      <!-- </v-flex> -->
    </v-layout>
  </v-toolbar>
</template>
<script>
export default {
  data() {
    return {
      navList: [{ name: "首页", link: "/" }],
      activeNav: true,
      searchContent: "",
      isActive: false
    };
  },
  methods: {}
};
</script>
<style lang="less" scoped>
@size: 72;
.hearder-container {
  max-width: 960px;
  margin: 0 auto !important;
  align-items: center;
}
.logo {
  display: inline-flex;
  height: 80%;
  img {
    height: 100%;
    width: auto;
  }
}
.nav {
  height: 100%;
  align-items: center;
  &-main {
    padding: 0 0.3rem;
    margin: 0;
    display: flex;
    height: 100%;
    align-items: center;
    li {
      padding: 0 0.3rem;
      font-size: 0.22rem;
      font-weight: 500;
      color: #71777c;
      &:hover {
        cursor: pointer;
        color: #007fff;
      }
    }
    &-active {
      color: #007fff;
    }
  }
  &-search {
    height: 0.4rem;
    border: 1px solid hsla(0, 0%, 59.2%, 0.2);
    background-color: rgba(227, 231, 236, 0.2);
    border-radius: 2px;
    display: flex;
    flex: initial;
    padding-left: 0.1rem;

    input {
      font-size: 0.16rem;
      flex-grow: 1;
      width: 1.4rem;
      color: #666;
    }
    i {
      width: 0.4rem;
      height: 0.4rem;
      flex-grow: 0;
    }
  }
  .active {
    border: 1px solid #007fff;
    i {
      color: #007fff;
    }
  }
  &-notify {
    padding: 0 20rem/@size;
  }
}
</style>