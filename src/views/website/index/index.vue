<template>
  <div style="height:100%">
    <el-carousel :autoplay="false" class="top-carousel" arrow="hover">
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
</template>

<script>
export default {
  name: "index"
};
</script>
<style scoped lang="scss">
.top-carousel {
  height: 100%;
  width: 100%;
  .carousel_item {
    height: 100%;
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
</style>
