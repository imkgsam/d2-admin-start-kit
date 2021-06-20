<template>
  <div class="container">
    <div class="suite_container">
      <div class="title">
        <h3>EMON SUITE</h3>
      </div>
      <el-row class="suite_item">
        <el-col :xs="24" :sm="12" class="suite_img fright">
          <!-- <span class="suite1"></span> -->
          <img src="@/assets/pictures/productlist/suite_01.jpg" />
          <div class="suite_img_title"><h3>suite 1</h3></div>
        </el-col>
        <el-col :xs="24" :sm="12" class="suite_desc fleft">
          <h3>CLINT</h3>
          <p>
            Lving on the leading edge of design and technology.The fuidlines and
            sleek silhouettes of product bring a minimalist lookto the bathroom
            that Complements a variety of decor.
          </p>
          <span>MORE</span>
        </el-col>
      </el-row>
      <el-row class="suite_item">
        <el-col :xs="24" :sm="12" class="suite_img fleft">
          <!-- <span class="suite1"></span> -->
          <img src="@/assets/pictures/productlist/suite_02.jpg" />
          <div class="suite_img_title"><h3>suite 2</h3></div>
        </el-col>
        <el-col :xs="24" :sm="12" class="suite_desc fright">
          <h3>CLINT</h3>
          <p>
            Lving on the leading edge of design and technology.The fuidlines and
            sleek silhouettes of product bring a minimalist lookto the bathroom
            that Complements a variety of decor.
          </p>
          <span>MORE</span>
        </el-col>
      </el-row>
    </div>
    <div class="subcat_container"></div>
  </div>
</template>

<script>
export default {
  name: "productlist",

  data() {
    return {};
  },
  computed: {}
};
</script>
<style scoped lang="scss">
.container * {
  transition: all 0.6s cubic-bezier(0.215, 0.61, 0.355, 1) 0s;
}
.container {
  padding: 65px 0;
  .title {
    padding-bottom: 55px;
    text-align: center;
    h3 {
      color: #333;
      font-size: 32px;
      line-height: 1;
      text-transform: uppercase;
    }
  }
  .suite_container {
    .suite_item {
      &:hover {
        background: #0eaee0;
      }
      margin: 0 1%;
      @media (min-width: $md) {
        margin: 0 5%;
      }
      padding-bottom: 10%;
      .suite_img {
        img {
          width: 100%;
        }
        .suite_img_title {
          font-size: 20px;
          text-align: center;
          display: block;
          @media (min-width: $md) {
            display: none;
          }
        }
      }
      .suite_desc {
        display: none;
        @media (min-width: $md) {
          display: block;
        }
        padding: 5% 5% 0 5%;
      }
    }
  }
}
.fright {
  float: right;
}
.fleft {
  float: left;
}
</style>
