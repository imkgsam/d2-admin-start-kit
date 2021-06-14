<template>
  <el-container>
    <el-header height="50px" style="background:lightgray">
      <div :class="['i_page', menuOpened ? 'openMenu' : '']">
        <div class="openBtn" @click="menuOpened = !menuOpened">
          <!-- <div class="lctext">MENU</div> -->
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
        <!-- drop down menu -->
        <div class="navMini">
          <div class="wrapper">
            <div class="content">
              <div class="nav_img">
                <a class="fl" href="room.php">
                  <div class="desc">
                    <div>
                      <h3>Bathroom Suite<span>More Details</span></h3>
                    </div>
                  </div>
                  <img src="images/nav_01.jpg" />
                </a>
                <a class="fr" href="productlist.php">
                  <div class="desc">
                    <div>
                      <h3>Products<span>More Details</span></h3>
                    </div>
                  </div>
                  <img src="images/nav_02.jpg" />
                </a>
              </div>
              <div class="nav_link">
                <a href="skill.php">Home</a>
                <a href="about.php">Company</a>
                <a href="news.php">Events</a>
                <a href="contact.php">Contact</a>
                <div class="search-box search-one">
                  <form action="product.php" method="get">
                    <input
                      type="text"
                      placeholder="Enter product number..."
                      name="search"
                      id="skey"
                      class="text"
                    />
                    <input
                      type="submit"
                      value=""
                      name="reset_input"
                      class="submit"
                    />
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </el-header>
    <el-main>
      <router-view :style="menuOpened ? 'position:fixed' : ''"></router-view>
    </el-main>
    <el-footer>
      footer
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
      menuOpened: false
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
  position: relative;
  top: 20px;
  right: 2%;
  cursor: pointer;
  z-index: 99;
  // .lctext {
  //   position: relative;
  //   float: left;
  //   color: #fff;
  //   margin-right: 20px;
  //   line-height: 25px;
  // }
  .lcbody {
    width: 40px;
    height: 24px;
    float: right;
    position: relative;
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
  -webkit-transform: translate3d(0, -100%, 0);
  transform: translate3d(0, -100%, 0);
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9;
  transition: all 0.6s cubic-bezier(0.215, 0.61, 0.355, 1) 0s;
  .wrapper {
    padding-top: 0;
    width: 100%;
    background: url("../../assets/pictures/menu_bg.jpg") no-repeat;
    background-size: cover;
    height: 100%;
    box-shadow: 0px 2px 6px rgb(0 0 0 / 10%);
  }
}

.openMenu {
  .openBtn {
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
</style>
