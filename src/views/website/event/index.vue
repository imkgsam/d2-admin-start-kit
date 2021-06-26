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
              <div class="event_img"><img :src="event.imgPath" /></div>
              <div class="event_content">
                <h3>{{ event.title }}</h3>
                <p>{{ event.content }}</p>
              </div>
              <div class="event_date">
                <span>{{ event.date.toISOString().split("T")[0] }}</span>
              </div>
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
          date: new Date(Date.parse("15 Jan 2020 GMT"))
        },
        {
          title: "Event 1 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: new Date(Date.parse("15 Jan 2020 GMT"))
        },
        {
          title: "Event 1 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: new Date(Date.parse("15 Jan 2020 GMT"))
        },
        {
          title: "Event 1 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: new Date(Date.parse("15 Jan 2020 GMT"))
        },
        {
          title: "Event 1 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: new Date(Date.parse("15 Jan 2020 GMT"))
        },
        {
          title: "Event 1 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: new Date(Date.parse("15 Jan 2020 GMT"))
        },
        {
          title: "Event 1 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: new Date(Date.parse("15 Jan 2020 GMT"))
        },
        {
          title: "Event 1 title",
          imgPath: "http://cleanman-cn.com/uploadimg/event_bimg.jpg",
          content: `Relying on local clay resource advantage and years" persistent operation in sanitary ware industry, Cleanman is committed to providing the highest level of customer service and a comprehensive product...`,
          date: new Date(Date.parse("15 Jan 2020 GMT"))
        }
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
  transition: all 0.4s cubic-bezier(0.215, 0.61, 0.355, 1) 0s;
}
.container {
  .title {
    height: 15%;
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
    @media (min-width: $lg) {
      height: calc(100vh - 80px);
      overflow: scroll;
    }
    width: 100%;
    background: white;
    .event_list_block {
      height: 100%;
      margin: 0 3%;
      @media (min-width: $lg) {
        margin: 0 8%;
      }
      .event_list {
        padding: 0;
        @media (min-width: $lg) {
          overflow: scroll;
        }
        height: 100%;
        margin: 0;
        .event_item {
          margin: 2% 2% 15% 2%;
          color: black;
          padding: 20px;
          box-shadow: 0 0 25px 0 rgb(0 0 0 / 10%);
          border-radius: 20px;
          overflow: hidden;
          @media (min-width: $lg) {
            margin: 2% 5% 2% 5%;
            &:hover {
              .event_img {
                overflow: hidden;
                img {
                  transform: scale(1.03, 1.03);
                }
              }
              .event_date {
                color: lightblue;
              }
              .event_content {
                transform: scale(1.03, 1.03);
              }
            }
          }
          a {
            width: 100%;
            text-decoration: none;
            color: inherit;
            display: inline-block;
            .event_img {
              width: 100%;
              float: left;
              img {
                width: 100%;
              }
              @media (min-width: $lg) {
                width: 45%;
                img {
                  width: 78%;
                }
              }
            }
            .event_content {
              float: left;
              text-align: center;
              width: 100%;
              h3 {
                margin: 3%;
                font-size: 25px;
              }
              p {
                margin: 3%;
              }
              @media (min-width: $lg) {
                width: 35%;
                h3 {
                  margin: 4% 0 0 0;
                  font-size: 32px;
                }
                p {
                  margin: 10% 3% 3% 3%;
                }
              }
            }
            .event_date {
              text-align: center;
              float: right;
              width: 100%;
              @media (min-width: $lg) {
                width: 15%;
                padding-top: 5%;
                text-align: left;
              }
              span {
                position: relative;
                top: 10%;
                font-size: 20px;
                @media (min-width: $lg) {
                  font-size: 30px;
                }
              }
            }
          }
        }
      }
    }
  }
}
</style>
