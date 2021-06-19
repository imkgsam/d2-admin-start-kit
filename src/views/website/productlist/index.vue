<template>
  <div class="container">
    <div class="suite_container">
      <div class="title">
        <h3>EMON SUITE</h3>
      </div>
      <div class="suite_list">
        <div class="suite_item">
          <router-link to="/index">
            <div class="suite_img float_l">
              <span class="suite1"></span>
            </div>
            <div class="suite_desc">
              <h3>CLINT</h3>
              <p>
                Lving on the leading edge of design and technology.The fuidlines
                and sleek silhouettes of product bring a minimalist lookto the
                bathroom that Complements a variety of decor.
              </p>
              <span>MORE</span>
            </div>
          </router-link>
        </div>
        <div class="suite_item">
          <router-link to="/index">
            <div class="suite_img float_r">
              <span class="suite2"> </span>
            </div>
            <div class="suite_desc">
              <h3>NATASHA</h3>
              <p>
                This collection is steeped in the traditions of classic
                Americandesign while embracing a modem eclectic
                sensibility.Thepeaceful bathroom is so cozy that makes people
                live afantastic high quality life.
              </p>
              <span>MORE</span>
            </div>
          </router-link>
        </div>
      </div>
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
    .suite_list {
      list-style-type: none;
      .suite_item {
        width: 100%;
        @media (min-width: $md) {
          width: 1400px;
          height: 430px;
        }
        margin: auto;
        margin-bottom: 35px;
        box-shadow: 0 0 60px 0 rgb(0 0 0 / 10%);
        &:hover {
          .suite_img span {
            transform: scale(1.05, 1.05);
          }
          .suite_desc {
            background: #0eaee0;
            h3 {
              color: #fff;
            }
            p {
              color: #a6d9f0;
            }
            span {
              width: 200px;
              border-color: #fff;
              color: #a6d9f0;
            }
          }
        }
        a {
          text-decoration: none;
          color: #555;
          line-height: 200%;
          .suite_img {
            float: left;
            width: 700px;
            height: 430px;
            overflow: hidden;
            background: url("../../../assets/logo/logo.png") center no-repeat
              #f8f8f8;
            span {
              display: block;
              width: 100%;
              height: 100%;
            }
            .suite1 {
              background-image: url("../../../assets/pictures/productlist/suite_01.jpg");
            }
            .suite2 {
              background-image: url("../../../assets/pictures/productlist/suite_02.jpg");
            }
          }
          .suite_desc {
            float: right;
            width: 700px;
            height: 430px;
            padding: 110px 140px 0 110px;
            box-sizing: border-box;
            background: #fff;
          }
          .float_l {
            float: left;
          }
          .float_r {
            float: right;
          }
        }
      }
    }
  }
}
</style>
