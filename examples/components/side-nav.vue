<style lang="less" type="text/less">
.el-scrollbar__wrap {
  overflow-x: hidden;
}
.side-nav {
  display: inline-block;
  margin: 32px 0;
  padding: 0;
  color: #3f536e;
  background-color: #fff;
  z-index: 99;
  .group-container {
    margin-bottom: 32px;
  }
  .side-nav-title {
    padding: 0 24px 8px;
    color: #8dabc4;
    font-size: 12px;
    font-weight: bold;
    letter-spacing: 1px;
    text-transform: uppercase;
  }
  .side-nav-items {
    font-size: 14px;
    font-weight: normal;
    line-height: 1.8;
    a {
      display: block;
      position: relative;
      padding: 8px 24px;
      color: #3f536e;
      font-weight: normal;
      line-height: 1.5;
      cursor: pointer;
    }
    .side-nav-group {
      display: block;
      position: relative;
      padding: 6px 0 6px 24px;
      color: #2c405a;
      font-weight: bold;
    }
    .slid-nav-component {
      display: block;
      position: relative;
      padding: 6px 24px 6px 32px;
      color: #616367;
      font-size: 14px;
    }
    .active {
      color: #3faaf5;
    }
  }
}
</style>
<template>
  <el-scrollbar style="height:100%">
    <div class="side-nav">
      <div v-for="title in (Object.keys(data))" class="group-container">
        <p class="side-nav-title">{{title}}</p>
        <div class="side-nav-items" v-for="nav in data[title]" v-if="nav.desc">
          <router-link :class="$route.name===nav.name ? 'active' : ''" v-if="nav.name" :to="{name: nav.name}">{{nav.desc}}</router-link>
          <p v-else class="side-nav-group">{{nav.desc}}</p>
          <div v-for="item in nav.items">
            <router-link :to="{name: item.name}" :class="$route.name===item.name ? 'active' : ''" class="slid-nav-component">{{item.desc}}</router-link>
          </div>
        </div>
      </div>
    </div>
  </el-scrollbar>
</template>

<script>
import navConf from "../nav.config.json";
export default {
  data() {
    return {
      data: navConf,
    };
  },
};
</script>
