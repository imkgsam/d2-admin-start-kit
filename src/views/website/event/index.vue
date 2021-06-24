<template>
  <div class="container">
    <div class="event_container">
      <div class="title">
        <h3>EVENTS</h3>
      </div>
      <div class="event_list_block">
        <ul class="event_list">
          <li v-for="(event, idx) in event_list" :key="idx">
            <div class="event_item">
              <h3>{{ event.title }}</h3>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "event",
  data() {
    return {
      event_list: [
        {
          title: "Event 1 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: Date.parse("15 Jan 2020 GMT")
        },
        {
          title: "Event 2 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: Date.parse("21 May 2021 GMT")
        }
      ]
    };
  },
  computed: {},
  mounted() {}
};
</script>
<style scoped lang="scss">
.container * {
  transition: all 0.6s cubic-bezier(0.215, 0.61, 0.355, 1) 0s;
}
.container {
  .title {
    h3 {
      font-size: 25px !important;
    }
    padding-top: 30px;
    padding-bottom: 15px;
    @media (min-width: $md) {
      padding-bottom: 0px;
      h3 {
        font-size: 32px !important;
      }
    }
    text-align: center;
    h3 {
      color: #333;
      font-size: 32px;
      line-height: 1;
      text-transform: uppercase;
    }
  }
  .event_container {
    height: 100vh;
    width: 100%;
    background-image: url("../../../assets/pictures/event/bg.jpeg");
    background-size: cover;
    background-repeat: no-repeat;
  }
}
</style>
