<template>
  <div id="app">
    <el-container class="wrapper">
      <app-header />
      <router-view/>
    </el-container>
  </div>
</template>

<script>
  import Header from "@/components/layout/HeaderPartial.vue";

  export default {
    components: {
      "app-header": Header,

    }
  }
</script>

<style lang="scss">
html, body {
  height: 100%;
}

body {
  font-family: 'Helvetica Neue',Helvetica,'PingFang SC','Hiragino Sans GB','Microsoft YaHei',SimSun,sans-serif;
}

* {
  padding: 0;
  margin: 0;
}

.wrapper {
  height: 100%;
}

a {
  text-decoration: none;
}
</style>
