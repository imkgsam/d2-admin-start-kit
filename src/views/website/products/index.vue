<template>
  <el-container style="margin-top:2%">
    <el-aside width="200px" class="asideNavBar">
      <div class="nav-container">
        <ul v-for="(cat, idx) in leftSideNav" :key="idx">
          <strong>{{ cat.title }}</strong>
          <li
            v-for="(f, i) in cat.children"
            :key="i"
            :class="$route.params.name === f.name ? 'navSelected' : ''"
          >
            <router-link :to="f.link + '/' + f.name">{{ f.name }}</router-link>
          </li>
        </ul>
      </div>
    </el-aside>
    <el-container>
      <el-main class="main">
        <div
          v-if="mainFilter && mainFilter.bannerSrc"
          class="banner"
          :style="[
            {
              background:
                'url(' + mainFilter.bannerSrc + ') no-repeat -50px -50px'
            },
            { height: '210px' }
          ]"
        ></div>
        <div class="top">
          <h2>{{ $route.params.name }}</h2>
          <div class="search-container">
            <input
              type="text"
              class="search_input"
              v-model="search_input"
              placeholder="SEARCH PRODUCTS"
            />
            <el-button
              plain
              icon="el-icon-search"
              :disabled="search_input === ''"
            ></el-button>
          </div>
        </div>

        <div class="filters" v-if="mainFilter">
          <el-dropdown
            class="filterGroup"
            size="medium"
            placement="bottom"
            v-for="(filter, idx) in mainFilter.filters"
            :key="idx"
          >
            <span class="el-dropdown-link">
              {{ filter.key }}<i class="el-icon-arrow-down el-icon--right"></i>
            </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item v-for="(op, i) in filter.options" :key="i">{{
                op
              }}</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <el-dropdown class="filterGroup" size="medium">
            <span class="el-dropdown-link">
              test<i class="el-icon-arrow-down el-icon--right"></i>
            </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item> </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <el-button
            class="filterGroup"
            type="text"
            icon="el-icon-s-operation"
            @click="allFilterdrawerOpened = true"
            >All Filters</el-button
          >
        </div>
        <el-drawer
          title="Filters"
          :visible.sync="allFilterdrawerOpened"
          class="filterDrawer"
        >
          <span>filters content</span>
        </el-drawer>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
import { chain } from "lodash";
export default {
  name: "products",
  methods: {},
  beforeUpdate() {
    console.log("in 　　beforeUpdate");
    if (this.$route.params.name) {
      let t = chain(this.leftSideNav)
        .map("children")
        .flatten()
        .filter({ name: this.$route.params.name })
        .value();
      console.log(t);
      if (t.length > 0) {
        this.mainFilter = t[0];
      } else {
        console.log("miss t");
      }
    }
    console.log(this.mainFilter);
  },
  created() {
    console.log("in created");
    if (!this.$route.params.name) {
      this.$router.push({ name: "products", params: { name: "all product" } });
    }
  },
  mounted() {
    console.log("in mounted");
    if (this.$route.params.name) {
      let t = chain(this.leftSideNav)
        .map("children")
        .flatten()
        .filter({ name: this.$route.params.name })
        .value();
      console.log(t);
      if (t.length > 0) {
        this.mainFilter = t[0];
      } else {
        console.log("miss t");
      }
    }
  },
  data() {
    return {
      allFilterdrawerOpened: false,
      mainFilter: null,
      drawer: false,
      search_input: "",
      leftSideNav: [
        {
          title: "all Products",
          children: [
            {
              lid: "A0",
              name: "all products",
              link: "/products",
              bannerSrc: "http://letop-cn.com/images/i_pro_01.jpg",
              filters: [
                {
                  key: "certification",
                  options: ["CUPC", "WATERMARK", "WATERSENSE", "CE"]
                },
                { key: "material", options: ["PP", "UF", "Metal", "Ceramic"] },
                { key: "color", options: ["white", "green", "red", "gold"] },
                { key: "target", options: ["children", "adult", "elder"] }
                //popularity,country,award....
              ]
            }
          ]
        },
        {
          title: "Toilets",
          children: [
            {
              lid: "T1",
              name: "all toilets",
              link: "/products",
              bannerSrc: "http://letop-cn.com/images/i_pro_02.jpg",
              filters: [
                {
                  key: "certification",
                  options: ["CUPC", "WATERMARK", "WATERSENSE", "CE"]
                },
                { key: "color", options: ["white", "green", "red", "gold"] },
                { key: "Trap", options: ["P-trap: 180mm", "S-trap:305mm"] }
              ]
            },
            {
              lid: "T2",
              name: "one piece toilet",
              link: "/products",
              filters: []
            },
            {
              lid: "T3",
              name: "two piece toilet",
              link: "/products",
              filters: []
            },
            {
              lid: "T4",
              name: "wall hung toilet",
              link: "/products",
              filters: []
            },
            {
              lid: "T5",
              name: "floor standing toilet",
              link: "/products",
              filters: []
            },
            {
              lid: "T6",
              name: "toilet cistern",
              link: "/products",
              filters: []
            },
            {
              lid: "T7",
              name: "high tank toilet",
              link: "/products",
              filters: []
            },
            {
              lid: "T8",
              name: "intelligent toilet",
              link: "/products",
              filters: []
            }
          ]
        },
        {
          title: "Sinks",
          children: [
            {
              lid: "S1",
              name: "all sinks",
              link: "/products",
              bannerSrc: "http://letop-cn.com/images/i_pro_03.jpg",
              filters: [
                {
                  key: "certification",
                  options: ["CUPC", "WATERMARK", "WATERSENSE", "CE"]
                },
                { key: "color", options: ["white", "green", "red", "gold"] },
                { key: "Trap", options: ["P-trap: 180mm", "S-trap:305mm"] }
              ]
            },
            {
              lid: "S2",
              name: "counter top sink",
              link: "/products",
              filters: []
            },
            {
              lid: "S3",
              name: "pedestal sink",
              link: "/products",
              filters: []
            },
            {
              lid: "S4",
              name: "wall hung sink",
              link: "/products",
              filters: []
            },
            {
              lid: "S5",
              name: "under counter sink",
              link: "/products",
              filters: []
            },
            { lid: "S6", name: "drop-in sink", link: "/products", filters: [] }
          ]
        },
        {
          title: "Bathwares",
          children: [
            {
              lid: "B1",
              name: "all bathwares",
              link: "/products",
              bannerSrc: "http://letop-cn.com/images/i_pro_04.jpg",
              filters: [
                {
                  key: "certification",
                  options: ["CUPC", "WATERMARK", "WATERSENSE", "CE"]
                },
                { key: "color", options: ["white", "green", "red", "gold"] },
                { key: "Trap", options: ["P-trap: 180mm", "S-trap:305mm"] }
              ]
            },
            { lid: "B2", name: "bathtub", link: "/products", filters: [] },
            { lid: "B3", name: "shower room", link: "/products", filters: [] },
            { lid: "B4", name: "shower panel", link: "/products", filters: [] },
            { lid: "B5", name: "shower head", link: "/products", filters: [] }
          ]
        },
        {
          title: "Others",
          children: [
            { lid: "O1", name: "all others", link: "/products", filters: [] },
            { lid: "O2", name: "toilet seat", link: "/products", filters: [] },
            { lid: "O3", name: "bidet seat", link: "/products", filters: [] },
            { lid: "O4", name: "urinal", link: "/products", filters: [] }
          ]
        },
        {
          title: "Accessories",
          children: [
            {
              lid: "A1",
              name: "all accessories",
              link: "/products",
              filters: []
            },
            { lid: "A2", name: "Wax ring", link: "/products", filters: [] },
            { lid: "A3", name: "drainer", link: "/products", filters: [] }
          ]
        }
      ]
    };
  },
  computed: {}
};
</script>
<style scoped lang="scss">
.asideNavBar {
  margin-top: 1%;
  display: none;
  @media (min-width: $md) {
    display: block;
  }
  .nav-container {
    ul {
      list-style-type: none;
      strong {
        font-size: 16px;
        line-height: 20px;
        color: #222;
        display: block;
        font-family: "Hiragino Kaku Gothic Pro", Osaka, "メイリオ", Meiryo,
          "MS PGothic", sans-serif;
        font-weight: bold;
        margin-bottom: 8px;
      }
      li {
        &:hover {
          text-decoration: underline;
          a {
            color: red;
          }
        }
        a {
          color: #222;
          display: block;
          font-size: 13px;
          line-height: 24px;
          text-decoration: none;
        }
      }
    }
  }
}
.navSelected {
  text-decoration: underline;
  a {
    color: red !important;
  }
}
.main {
  .top {
    display: block;
    width: 100%;

    h2 {
      font-size: 30px;
      text-transform: capitalize;
    }
    .search-container {
      display: none;
    }
    @media (min-width: $md) {
      display: inline-flex;
      justify-content: space-between;
      h2 {
        margin-left: 3%;
        font-size: 48px;
        text-transform: capitalize;
      }
      .search-container {
        height: fit-content;
        display: inline-flex;
        margin: auto 0;
        border: 1px solid black;
        width: fit-content;
        border-radius: 20px;
        overflow: hidden;
        .search_input {
          border: 0;
          padding: 10px 30px 10px 20px;
          &:focus {
            outline: none;
          }
        }
        button {
          border: none;
        }
      }
    }
  }
  .banner {
    width: 100%;
    // overflow: hidden;
    img {
      width: 100%;
    }
  }
  .filters {
    margin-left: 3%;
    .filterGroup {
      margin-right: 30px;
      color: #222;
      span {
        text-transform: capitalize;
      }
    }
    button.filterGroup {
      text-decoration: none;
    }
  }
  .filterDrawer {
    ::v-deep .el-drawer__container {
      .el-drawer {
        width: 100% !important;
        @media (min-width: $md) {
          width: 30% !important;
        }
      }
    }
  }
}
</style>
