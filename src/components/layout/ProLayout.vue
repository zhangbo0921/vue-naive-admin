<template>
  <n-layout class="unvue-pro-layout">
    <n-layout-header class="unvue-header">颐和园路</n-layout-header>
    <n-layout has-sider>
      <n-layout-sider class="unvue-sider"> 海淀桥 </n-layout-sider>
      <n-layout-content class="unvue-content">
        <n-input v-model:value="height"></n-input>
        <n-button @click="setColor">切换</n-button>
        <n-space>
          <RouterLink to="/">dashboard</RouterLink>
          <RouterLink to="/dashboard/settings">settings</RouterLink>
        </n-space>
        <RouterView></RouterView>
      </n-layout-content>
    </n-layout>
  </n-layout>
</template>
<script setup lang="ts">
import { ref } from 'vue'
const height = ref(64)
const setColor = () => {
  console.log(height.value)
  document.documentElement.style.setProperty('--layout-header-height', height.value + 'px')
}
</script>
<style lang="less">
@import url('@/less/var.less');
.unvue-pro-layout {
  .unvue-header {
    background-color: beige;
    height: @layout-header-height;
  }
  .unvue-sider {
    background-color: rgb(212, 249, 223);
    height: calc(100vh - @layout-header-height);
  }
  .unvue-content {
    background-color: rgb(212, 228, 249);
  }
}
</style>
