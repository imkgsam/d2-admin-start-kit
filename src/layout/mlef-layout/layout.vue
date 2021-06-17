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
        <div class="links_s">
          <el-collapse accordion>
            <el-collapse-item title="title1">
              <ul>
                <li><router-link to="/index">link1</router-link></li>
                <li><router-link to="/index">link2</router-link></li>
                <li><router-link to="/index">link3</router-link></li>
                <li><router-link to="/index">link4</router-link></li>
              </ul>
            </el-collapse-item>
            <el-collapse-item title="title2">
              <ul>
                <li><router-link to="/index">link1</router-link></li>
                <li><router-link to="/index">link2</router-link></li>
                <li><router-link to="/index">link3</router-link></li>
                <li><router-link to="/index">link4</router-link></li>
              </ul>
            </el-collapse-item>
            <el-collapse-item title="title3">
              <ul>
                <li><router-link to="/index">link1</router-link></li>
                <li><router-link to="/index">link2</router-link></li>
                <li><router-link to="/index">link3</router-link></li>
                <li><router-link to="/index">link4</router-link></li>
              </ul>
            </el-collapse-item>
            <el-collapse-item title="title4">
              <ul>
                <li><router-link to="/index">link1</router-link></li>
                <li><router-link to="/index">link2</router-link></li>
                <li><router-link to="/index">link3</router-link></li>
                <li><router-link to="/index">link4</router-link></li>
              </ul>
            </el-collapse-item>
          </el-collapse>
        </div>
        <div class="links_b"></div>
        <ul class="socialmedias">
          <li>
            <a href="" target="_blank">
              <img src="@/assets/pictures/social_16/fb_16.png" />
            </a>
          </li>
          <li>
            <a href="" target="_blank">
              <img src="@/assets/pictures/social_16/ins_16.png" />
            </a>
          </li>
          <li>
            <a href="" target="_blank">
              <img src="@/assets/pictures/social_16/li_16.png" />
            </a>
          </li>
          <li>
            <a href="" target="_blank">
              <img src="@/assets/pictures/social_16/tw_16.png" />
            </a>
          </li>
          <li>
            <a href="" target="_blank">
              <img src="@/assets/pictures/social_16/yt_16.png" />
            </a>
          </li>
        </ul>
        <div :class="['copyright', readmore ? '' : 'truncated']">
          <p>
            The content of this site is copyright-protected and is the property
            of H&M Hennes & Mauritz AB. H&M is committed to accessibility. That
            commitment means H&M embraces WCAG guidelines and supports assistive
            technologies such as screen readers. If you are using a screen
            reader, magnifier, or other assistive technologies and are
            experiencing difficulties using this website, please call our
            TOLL-FREE support line (855-466-7467) for assistance. H&M's business
            concept is to offer fashion and quality at the best price. H&M has
            since it was founded in 1947 grown into one of the world's leading
            fashion companies.
          </p>
          <el-button type="text" @click="readmore = !readmore">{{
            readmore ? "READ LESS" : "READ MORE"
          }}</el-button>
        </div>
        <div class="logo">
          <router-link to="/index"> </router-link>
        </div>
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
      search_input: "",
      readmore: false
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
  $footer_bg_color: #e4e4e4;
  padding: 0;
  .layout {
    background-color: $footer_bg_color;
    .links_s {
      @media (min-width: $md) {
        display: none;
      }
      margin: 0 15px;
      ::v-deep{
        .el-collapse {
          box-sizing: border-box;
          padding-left: 25px;
          border: none;
          .el-collapse-item__header {
            border: none;
            background-color: transparent;
          }
          .el-collapse-item__wrap {
            background-color: transparent;
            border: none;
            .el-collapse-item__content {
              padding: 0;
              ul{
                list-style-type:none;
                padding-left: 25px;
                li a {
                  font-size: 13px;
                  line-height: 15px;
                  color:#333;
                }
              }
            }
          }
        }
      }
    }
    .links_b {
      display: none;
      background: transparent;
      @media (min-width: $md) {
        display: block;
      }
      margin: 0 15px;
      .el-collapse-item__content ul {
        list-style-type: none;
      }
    }
    .socialmedias {
      list-style-type: none;
      display: flex;
      justify-content: space-around;
      width: 240px;
      margin: 5% auto;
      padding: 0;
      @media (min-width: $md) {
        margin: 3% auto 2% auto;
      }
    }
    .copyright {
      text-align: center;
      margin: 0 auto;
      font-size: 12px;
      button {
        padding-top: 6px;
        color: #777;
      }
      p {
        max-width: 700px;
        margin: 0;
        text-overflow: none;
        white-space: none;
        overflow: none;
        padding: 0 44px;
        margin: 0 auto;
      }
    }
    .truncated {
      p {
        width: 70%;
        text-overflow: ellipsis;
        white-space: nowrap;
        overflow: hidden;
      }
    }
    .logo {
      margin: 19px auto 0 auto;
      padding-bottom: 80px;
      a {
        background: url("data:image/svg+xml;charset=US-ASCII,%3Csvg%20width%3D%22323%22%20height%3D%2242%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20xmlns%3Axlink%3D%22http%3A%2F%2Fwww.w3.org%2F1999%2Fxlink%22%3E%3Ctitle%3E209A409D-4D20-46EE-9778-57304659E282%401.00x%3C%2Ftitle%3E%3Cdefs%3E%3Cpath%20d%3D%22M172.407%201.439c.031%201.497-.19%203.483-.347%204.925-.855%207.82-2.284%2014.21-2.393%2022.24%203.762-9.78%206.92-16.575%2010.982-24.947%201.29-2.663%202.112-2.168%203.173-2.642%204.129-1.844%204.284-.71%203.744%201.542-2.004%208.358-7.125%2034.668-7.908%2038.718-.228%201.173-1.496.676-1.826.218-1.47-2.04-3.126-2.071-2.94-3.428.922-6.756%204.238-23.702%205.102-27.695-4.41%209.072-8.98%2020.412-11.327%2026.842-.497%201.365-1.404%201.266-1.969.266-.794-1.403-2.333-2.12-2.588-3.778-.807-5.273.922-15.323%201.162-21.68-2.4%206.944-6.429%2020.429-8.194%2026.522-.73%202.52-3.152%202.11-2.508-.348%202.682-10.224%208.459-28.307%2010.96-34.81.589-1.527%202.127-1.475%203.406-2.108%202.302-1.14%203.446-.988%203.471.163zm-22.522-.145c1.387-.239%203.644-1.463%204.424-1.274.73.176.671%201.04.225%202.222-1.318%203.486-3.145%208.065-5.234%2013.465%201.314-.15%202.027-.2%202.027-.2%201.884-.235%202.236.711%201.705%201.719-.423.803-.933.268-2.696%202.907-.996%201.488-2.617%201.881-3.519%202.08-2.172%205.77-4.497%2012.208-6.76%2019.07-.328.998-1.289.78-1.578.373-1.062-1.489-1.845-1.537-2.67-2.741-.097-.195-.291-.46-.174-.939.605-2.484%202.212-7.586%204.657-14.304-3.08.67-6.412%201.39-7.787%201.712a614.858%20614.858%200%200%200-4.786%2013.114c-.946%202.693-3.41%202.172-2.545-.372a442.816%20442.816%200%200%201%204.42-12.348c-1.706-.182-2.283-1.392-3.236-2.402-.369-.391-1.172-.336-1.564-.883-.708-.984-.637-1.42.996-1.893a161.61%20161.61%200%200%201%206.425-1.721c2.76-7.149%205.253-13.281%206.582-16.553%201.024-2.522%203.665-2.287%202.662.2-2.039%205.055-4.13%2010.307-6.192%2015.632%202.885-.65%205.467-1.148%207.673-1.527a396.956%20396.956%200%200%201%205.937-14.456c.145-.333.568-.806%201.008-.88zm1.624%2029.78c.169-.163.334-.323.494-.461%201.134-.985%202.215-.008%201.095%201.658-.24.358-.514.742-.812%201.122.141.404.268.754.369%201.012.578%201.49-.94%201.863-1.431.63l-.135-.346c-.923.821-1.991%201.34-3.132.984-1.88-.586-2.356-3.241-.602-5.287a38.362%2038.362%200%200%201%201.675-1.844%2043.18%2043.18%200%200%201-.312-1.062c-.228-.829-.434-1.794.392-2.777%201.547-1.845%205.14-.208%203.323%202.631-.438.684-.95%201.33-1.484%201.985.178.566.369%201.164.56%201.755zM10.519%2021.29H2.147v7.165H0V13.256h2.147v5.971h8.372v-5.97h2.147v15.198h-2.147V21.29zm17.171-2.063v2.063h-4.936v5.102h6.654v2.064h-8.8v-15.2h8.585v2.062h-6.44v3.91h4.937zm10.71-1.932v11.16h-2.146V13.256h1.501l9.017%2011.161v-11.16h2.147v15.198h-1.502L38.4%2017.295zm20.607%200v11.16h-2.146V13.256h1.501l9.015%2011.161v-11.16h2.148v15.198h-1.503l-9.015-11.16zm25.543%201.932v2.063h-4.937v5.102h6.654v2.064h-8.802v-15.2h8.588v2.062h-6.44v3.91h4.937zm8.778%205.429c.88%201.085%202.124%201.954%203.67%201.954%201.396%200%202.62-.912%202.62-2.28%200-2.323-3.178-2.584-5.174-3.91-1.074-.716-1.911-1.758-1.911-3.343%200-2.214%201.932-4.038%204.55-4.038%201.912%200%203.242.847%204.038%201.52l-1.267%201.585c-.816-.695-1.74-1.042-2.683-1.042-1.246%200-2.49.716-2.49%202.04%200%201.933%203.197%202.345%205.13%203.649%201.009.673%201.953%201.736%201.953%203.474%200%202.67-2.04%204.407-4.657%204.407-2.062%200-3.93-.912-5.26-2.54l1.481-1.476zm124.56.542h-1.502l-4.4-6.97v10.227h-2.147V13.256h1.503l5.795%209.271%205.796-9.27h1.502v15.198h-2.147V18.228l-4.4%206.97zm31.98-3.04v-8.902h2.147v9.01c0%201.434.344%202.324.945%202.997.752.847%201.868%201.347%203.134%201.347%201.267%200%202.383-.5%203.134-1.347.601-.673.945-1.563.945-2.997v-9.01h2.147v8.903c0%202.04-.601%203.452-1.567%204.516-1.138%201.237-2.813%201.997-4.659%201.997-1.846%200-3.52-.76-4.659-1.997-.965-1.064-1.566-2.475-1.566-4.516zm-9.184%202.389h-6.334l-1.567%203.909h-2.232l6.225-15.2h1.503l6.226%2015.2h-2.234l-1.587-3.91zm-5.475-2.063h4.637l-2.318-5.646-2.319%205.646zm52.631%205.97V13.257h2.147v15.199h-2.147zm8.457-15.198H306.6v2.063h-4.078v13.136h-2.146V15.319h-4.08v-2.063zm16.184%200h10.089v1.411l-7.813%2011.725H323v2.063h-11.162v-1.411l7.856-11.725h-7.213v-2.063zm-40.288%208.034v7.166h-2.147v-15.2h5.26c1.374%200%202.232.325%202.918.89a4.032%204.032%200%200%201%201.481%203.127c0%201.26-.577%202.389-1.48%203.127a3.588%203.588%200%200%201-1.76.803l5.387%207.253h-2.597l-5.345-7.166h-1.717zm3.006-2.063c.966%200%201.458-.217%201.803-.564.343-.348.557-.848.557-1.39%200-.542-.214-1.043-.557-1.39-.345-.348-.837-.565-1.803-.565h-3.006v3.91h3.006zm-125.924%2012.21c-.924%201.274-.377%201.727.31%201.306.217-.133.432-.296.646-.474-.164-.48-.326-.97-.481-1.45-.16.205-.32.405-.475.619zm1.047-4.2c.16-.167.32-.337.491-.532%201.144-1.295-1.117-1.838-.596.145.028.11.065.244.105.386z%22%20id%3D%22prefix__a%22%2F%3E%3C%2Fdefs%3E%3Cuse%20fill%3D%22%23222%22%20xlink%3Ahref%3D%22%23prefix__a%22%20fill-rule%3D%22evenodd%22%2F%3E%3C%2Fsvg%3E")
          no-repeat;
        background-position: center;
        background-size: contain;
        display: block;
        margin: 0 auto;
        width: 170px;
        display: block;
        height: 26px;
      }
    }
  }
}
</style>
