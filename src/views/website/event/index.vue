<template>
  <div class="container">
    <div class="event_container">
      <div class="title">
        <h3>EVENTS</h3>
      </div>
      <div class="event_list_block">
        <div class="event_list">
          <div v-for="(event, idx) in event_list" :key="idx" class="event_item">
            <router-link to="/index">
              <div class="event_img">1</div>
              <div class="event_content">2</div>
              <div class="event_date">3</div>
            </router-link>
          </div>
        </div>
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
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {},
        {}
      ]
    };
  },
  computed: {},
  mounted() {},
  methods: {}
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
    height: calc(100vh - 60px);
    width: 100%;
    background-image: url("../../../assets/pictures/event/bg.jpeg");
    background-size: cover;
    background-repeat: no-repeat;
    .event_list_block {
      height: 75%;
      background: white;
      margin: 0 8%;
      .event_list {
        padding: 0;
        overflow: scroll;
        height: 100%;
        margin: 0;
        .event_item {
          border: 1px solid black;
          padding: 10px;
          a {
            text-decoration: none;
            color: inherit;
            display: inline-block;
            .event_img {
              float: left;
            }
            .event_content {
              float: left;
            }
            .event_date {
              float: right;
            }
          }
        }
      }
    }
  }
}
</style>
