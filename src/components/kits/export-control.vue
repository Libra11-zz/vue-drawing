<!--
 * @Author: Libra
 * @Date: 2021-07-16 13:53:26
 * @LastEditTime: 2021-07-28 17:01:41
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
  width: 600px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
.insert {
  width: 80px;
  height: 40px;
  margin-top: 10px;
  background-color: #fff;
  color: #000;
  cursor: pointer;
  display: flex;
  border: 1px solid #ccc;
  border-radius: 5px;
  justify-content: center;
  align-items: center;
}
.insert:hover {
  background-color: #dd0000;
  border: none;
  color: #fff;
}
</style>
