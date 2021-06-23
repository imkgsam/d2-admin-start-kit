<template>
  <div>
    <div class="carousel-container_b">
      <el-carousel
        :autoplay="false"
        class="top-carousel"
        height="100%"
        arrow="hover"
      >
        <el-carousel-item class="carousel_item video_container">
          <video ref="video" muted loop>
            <source src="@/assets/video/banner_video.mp4" type="video/mp4" />
          </video>
        </el-carousel-item>
        <el-carousel-item class="carousel_item"
          ><router-link to="/index" class="pic1"></router-link>
        </el-carousel-item>
        <el-carousel-item class="carousel_item"
          ><router-link to="/index" class="pic2"></router-link>
        </el-carousel-item>
        <el-carousel-item class="carousel_item"
          ><router-link to="/index" class="pic3"></router-link>
        </el-carousel-item>
      </el-carousel>
    </div>
    <div class="carousel-container_s">
      <swiper ref="mySwiper" :options="swiperOptions">
        <swiper-slide
          ><a><img src="@/assets/pictures/index/mobile/wx01.jpg"/></a
        ></swiper-slide>
        <swiper-slide
          ><a><img src="@/assets/pictures/index/mobile/wx02.jpg"/></a
        ></swiper-slide>
        <swiper-slide
          ><a><img src="@/assets/pictures/index/mobile/wx03.jpg"/></a
        ></swiper-slide>
        <swiper-slide
          ><a><img src="@/assets/pictures/index/mobile/wx04.jpg"/></a
        ></swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
    <!-- <el-backtop target=".page-component__scroll .el-scrollbar__wrap"></el-backtop> -->
  </div>
</template>

<script>
export default {
  name: "index",
  methods: {
    setVideoAutoPlayAttr() {
      console.log("in setVideoAutoPlayAttr");
      let screenWidth = window.innerWidth;
      console.log("screenwidth: ", screenWidth);
      console.log("refs ", this.$refs);
      if (screenWidth < 768) {
        this.$refs["video"].removeAttribute("autoplay");
      } else {
        this.$refs["video"].setAttribute("autoplay", "autoplay");
      }
    },
    onSwiper(swiper) {
      console.log(swiper);
    },
    onSlideChange() {
      console.log("slide change");
    }
  },
  mounted() {
    console.log("in mounted");
    this.setVideoAutoPlayAttr();
  },
  destroyed() {
    console.log("in destroyed");
  },
  data() {
    return {
      video_loading: true,
      loadingInstance: null,
      swiperOptions: {
        pagination: {
          el: ".swiper-pagination"
        }
      }
    };
  },
  computed: {
    swiper() {
      return this.$refs.mySwiper.$swiper;
    }
  }
};
</script>
<style scoped lang="scss">
.carousel-container_b {
  display: none;
  @media (min-width: $md) {
    display: block;
  }
  height: calc(100vh - 60px);
  min-height: calc(100vh - 60px);
  .top-carousel {
    div.el-carousel__container {
      height: 100% !important;
    }
    .video_container {
      display: none;
      @media (min-width: $md) {
        display: block;
      }
    }
    height: calc(100vh - 60px);
    width: 100%;
    .carousel_item {
      height: calc(100vh - 60px);
      min-height: calc(100vh - 60px);
      width: 100%;
      a {
        display: block;
        width: 100%;
        height: 100%;
        overflow: hidden;
        background-size: cover;
        position: relative;
        background-repeat: no-repeat;
        background-position: center;
      }
      a.pic1 {
        background-image: url("../../../assets/pictures/banner1.jpg");
      }
      a.pic2 {
        background-image: url("../../../assets/pictures/banner2.jpg");
      }
      a.pic3 {
        background-image: url("../../../assets/pictures/banner3.jpg");
      }
    }
  }
}
.carousel-container_s {
  @media (min-width: $md) {
    display: none;
  }
  width: 100%;
  .swiper-container {
    .swiper-wrapper {
      .swiper-slide {
        a img {
          width: 100%;
        }
      }
    }
  }
}
</style>
