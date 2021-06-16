<template>
  <el-container>
    <el-main style="padding:0">
      <div
        :class="[
          'i_page',
          menuOpened ? 'openMenu' : '',
          searchBarOpened ? '' : 'openSearchBar'
        ]"
      >
        <div
          class="shade_layer"
          @click="searchBarOpened = !searchBarOpened"
        ></div>
        <transition name="fade">
          <div class="search_bar" v-if="searchBarOpened">
            <input
              type="text"
              class="search_input"
              v-model="search_input"
              placeholder="SEARCH PRODUCTS"
            />
            <el-button
              plain
              icon="el-icon-close"
              @click="
                searchBarOpened = false;
                search_input = '';
              "
            >
            </el-button>
            <el-divider class="divider" direction="vertical"></el-divider>
            <el-button
              plain
              icon="el-icon-search"
              :disabled="search_input === ''"
            ></el-button>
          </div>
        </transition>
        <div class="openBtn" @click="menuOpened = !menuOpened">
          <div class="lcbody">
            <div class="lcitem top">
              <div class="rect"></div>
            </div>
            <div class="lcitem center">
              <div class="rect"></div>
            </div>
            <div class="lcitem bottom">
              <div class="rect"></div>
            </div>
          </div>
        </div>
        <div class="header_logo">
          <router-link to="/index">
            <img src="@/assets/pictures/logo_white.png" />
          </router-link>
        </div>
        <div class="header_nav">
          <ul>
            <li>
              <router-link to="/index">Home</router-link>
            </li>
            <li>
              <router-link to="/index">Company</router-link>
            </li>
            <li>
              <router-link to="/index">Events</router-link>
            </li>
            <li>
              <router-link to="/index">Contact</router-link>
            </li>
          </ul>
        </div>
        <el-button
          type="text"
          icon="el-icon-search"
          class="search_btn"
          @click="searchBarOpened = !searchBarOpened"
          >Search</el-button
        >
        <!-- drop down menu -->
        <div class="navMini">
          <div class="wrapper">
            <div class="menu_search">
              <input placeholder="Search Products..." v-model="search_input" />
              <el-button
                icon="el-icon-search"
                size="medium"
                :disabled="search_input === ''"
              ></el-button>
            </div>
            <div class="navbar">
              <ul>
                <li>
                  <router-link to="/index">Home</router-link>
                </li>
                <li>
                  <router-link to="/index">Company</router-link>
                </li>
                <li>
                  <router-link to="/index">Events</router-link>
                </li>
                <li>
                  <router-link to="/index">Contact</router-link>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <router-view
        :style="menuOpened ? 'position:fixed;width:100%' : ''"
      ></router-view>
    </el-main>

    <el-footer class="footer">
      <div class="layout">
        <div class="links"></div>
        <ul class="socialmedias">
          <li class="item">
            <a
              href="https://www.facebook.com/hmtheus"
              target="_blank"
              rel="noopener noreferrer"
              title="Facebook"
              class="hidden-text icon icon-social-facebook-white"
            >
              Facebook
            </a>
          </li>
          <li class="item">
            <a
              href="https://twitter.com/hmusa"
              target="_blank"
              rel="noopener noreferrer"
              title="Twitter"
              class="hidden-text icon icon-social-twitter-white"
            >
              Twitter</a
            >
          </li>
          <li class="item">
            <a
              href="https://www.instagram.com/hm/"
              target="_blank"
              rel="noopener noreferrer"
              title="Instagram"
              class="hidden-text icon icon-social-instagram-white"
            >
              Instagram</a
            >
          </li>
          <li class="item">
            <a
              href="http://www.youtube.com/user/hennesandmauritz"
              title="Youtube"
              target="_blank"
              rel="noopener noreferrer"
              class="hidden-text icon icon-social-youtube-white"
            >
              Youtube</a
            >
          </li>
          <li class="item">
            <a
              href="https://www.pinterest.com/hm/"
              target="_blank"
              rel="noopener noreferrer"
              title="Pinterest"
              class="hidden-text icon icon-social-pinterest-white"
            >
              Pinterest</a
            >
          </li>
        </ul>
        <div class="socialmedias"></div>
        <div class="copyright"></div>
        <div class="logo"></div>
      </div>
    </el-footer>
  </el-container>
</template>

<script>
// import { mapState, mapActions, mapGetters } from "vuex";
// import { capitalize } from "@/utils";
// import { map } from "lodash";
export default {
  name: "layout",
  data() {
    return {
      menuOpened: false,
      searchBarOpened: false,
      search_input: ""
    };
  },
  computed: {},
  mounted() {},
  methods: {}
};
</script>

<style scoped lang="scss">
@keyframes move {
  0% {
    right: 0;
  }
  40% {
    right: 0;
    width: 0;
  }
  60% {
    right: auto;
    width: 0%;
  }
  100% {
    right: auto;
    width: 100%;
  }
}
.openBtn {
  display: block;
  position: absolute;
  top: 20px;
  left: 2%;
  cursor: pointer;
  z-index: 5;
  @media (min-width: $md) {
    display: none;
  }
  .lcbody {
    width: 30px;
    height: 18px;
    float: right;
    position: relative;
    @media (min-width: $md) {
      width: 40px;
      height: 24px;
    }
    .lcitem {
      width: 100%;
      height: 3px;
      position: absolute;
      transition: transform 0.36s ease;
      left: 0;
      right: 0;
      div {
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
        left: auto;
        right: 0;
        background: #fff;
      }
    }
    .top {
      top: 0;
    }
    .center {
      margin: 0 auto;
      width: 60%;
      top: 49%;
    }
    .bottom {
      top: 100%;
    }
    &:hover {
      .top .rect {
        animation: move 0.4s ease-in-out 1;
      }
      .center .rect {
        animation: move 0.4s ease-in-out 0.1s 1;
      }
      .bottom .rect {
        animation: move 0.4s ease-in-out 0.2s 1;
      }
    }
  }
}
.navMini {
  position: fixed;
  top: 0;
  width: 100%;
  height: 100vh;
  text-align: center;
  padding-top: 0;
  overflow: hidden;
  visibility: hidden;
  transform: translate3d(0, -100%, 0);
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
  transition: all 0.6s cubic-bezier(0.215, 0.61, 0.355, 1) 0s;
  .wrapper {
    padding-top: 0;
    width: 100%;
    background: #000;
    height: 100%;
    box-shadow: 0px 2px 6px rgb(0 0 0 / 10%);
    .navbar {
      display: flex;
      margin-top: 3%;
      justify-content: space-around;
      // float: left;
      // width: 70%;
      // margin-left: 5%;
      ul {
        list-style-type: none;
        text-align: center;
        padding: 0;
        li {
          margin: 3% 0;
          a {
            font-size: 25px;
            color: #ccc;
            &:hover {
              color: #ddd;
              text-decoration: underline;
            }
          }
        }
      }
    }
    .menu_search {
      padding-top: 60px;
      width: 100%;
      button {
        background: transparent;
        border: none;
        color: #ccc;
        font-size: 26px;
      }
      input {
        color: #ddd;
        padding: 2%;
        margin-top: 8%;
        font-size: 20px;
        width: 70%;
        border-radius: 15px;
        background: #333;
        border: none;
        &:focus {
          outline: none;
        }
      }
    }
  }
}
.openMenu {
  .header_logo {
    position: fixed;
  }
  .openBtn {
    position: fixed;
    .lcitem.top {
      transform: rotateZ(45deg);
      top: 49%;
    }
    .lcitem.center {
      opacity: 0;
    }
    .lcitem.bottom {
      transform: rotateZ(-45deg);
      top: 49%;
    }
  }
  .navMini {
    visibility: visible;
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    opacity: 1;
  }
}
.header {
  padding: 0;
  background: rgba(0, 0, 0, 0.8);
}
.i_page {
  display: flex;
  background: #888;
  height: 60px;
}
.header_nav {
  display: none;
  width: 80%;
  ul {
    list-style-type: none;
    width: 100%;
    display: inline-block;
    float: right;
    li {
      padding-right: 20px;
      float: right;
      line-height: 26px;
      box-sizing: border-box;
      display: block;
      position: relative;
      z-index: 1;
      vertical-align: top;
      a {
        color: #ccc;
        &:hover {
          color: #ddd;
        }
      }
    }
  }
  @media (min-width: $md) {
    display: flex;
  }
}
.header_logo {
  z-index: 4;
  // margin: auto;
  width: 100%;
  text-align: center;
  padding-top: 10px;
  padding-left: 0;
  @media (min-width: $md) {
    width: 10%;
    padding-left: 30px;
  }
}
.search_btn {
  display: none;
  color: #ccc;
  @media (min-width: $md) {
    display: block;
  }
  &:hover {
    color: #ddd;
  }
}
.search_bar {
  position: fixed;
  width: 100%;
  height: 60px;
  background: white;
  z-index: 10;
  button {
    height: 100%;
    float: right;
    border: none;
    background: none;
    font-size: 28px;
  }
  @media (min-width: $md) {
    display: block;
  }
  .divider {
    float: right;
    height: 100%;
  }
  .search_input {
    margin-left: 25px;
    margin-top: 18px;
    font-size: 17px;
    border: none;
    width: 75%;
    outline: none;
  }
}
.openSearchBar .search_bar {
  display: none;
}
.openSearchBar .shade_layer {
  display: none;
}

.shade_layer {
  position: fixed;
  width: 100%;
  height: 100%;
  overflow: hidden;
  background: #111;
  opacity: 0.6;
  z-index: 9;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

//footer style
.footer {
  padding: 0;
  .layout {
    .links {
    }
    .socialmedias {
    }
    .copyright {
    }
    .logo {
    }
  }
}
</style>
