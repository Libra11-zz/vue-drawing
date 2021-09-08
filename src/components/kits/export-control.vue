<!--
 * @Author: Libra
 * @Date: 2021-07-16 13:53:26
 * @LastEditTime: 2021-07-29 17:19:20
 * @LastEditors: Libra
 * @Description: 
 * @FilePath: /vue-drawing/src/components/kits/export-control.vue
-->
<template>
  <div class="insert-container">
    <div class="insert">
      插入
    </div>
  </div>
</template>

<script>
  export default {
    name: "export-control"
  };
</script>

<style scoped>
.insert-container {
  width: 900px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
.insert {
  width: 80px;
  height: 40px;
  margin-top: 10px;
  background-color: #dd0000;
  color: #fff;
  cursor: pointer;
  display: flex;
  border-radius: 5px;
  justify-content: center;
  align-items: center;
}
.insert:hover {
  background-color: rgba(255, 0, 0, 0.8);
}
</style>
