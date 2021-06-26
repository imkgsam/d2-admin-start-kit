<template>
  <div class="container">
    <el-radio-group class="filters" v-model="cat.value">
      <el-radio-button
        circle
        class="ops"
        v-for="(op, idx) in cat.options"
        :key="idx"
        :label="op"
      >
      </el-radio-button>
      <el-button
        @click="drawer = !drawer"
        style="position:fixed;right:0;"
        :icon="drawer ? 'el-icon-arrow-right' : 'el-icon-arrow-left'"
      ></el-button>
    </el-radio-group>
    <el-drawer
      title="我是标题"
      :visible.sync="drawer"
      :with-header="false"
      size="50%"
    >
      <span>我来啦!</span>
    </el-drawer>
  </div>
</template>

<script>
export default {
  name: "products",
  methods: {},
  mounted() {},
  destroyed() {},
  data() {
    return {
      drawer: false,
      cat: {
        key: "Cat",
        value: "All",
        options: ["Toilets", "Sinks", "Bathwares", "Others", "All"].sort()
      }
    };
  },
  computed: {}
};
</script>
<style scoped lang="scss">
.container {
  .filters {
    display: block;
    .ops {
    }
  }
}
</style>
