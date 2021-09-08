<!--
 * @Author: Libra
 * @Date: 2021-07-16 13:53:26
 * @LastEditTime: 2021-07-29 17:16:01
 * @LastEditors: Libra
 * @Description: 
 * @FilePath: /vue-drawing/src/App.vue
-->
<template>
  <Main :width="900" :height="400"></Main>
</template>

<script>
  import Main from "./components/Main";

  export default {
    name: "app",
    components: { Main }
  };
</script>

<style lang="scss"></style>
