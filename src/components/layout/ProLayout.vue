<template>
  <n-layout class="unvue-pro-layout" :has-sider="isMix">
    <n-layout-header class="unvue-header" v-if="isSider">Header</n-layout-header>
    <n-layout-sider class="unvue-sider" v-if="isMix" :style="{ height: '100vh' }">
      Sider
    </n-layout-sider>
    <n-layout :has-sider="isSider">
      <n-layout-sider class="unvue-sider" v-if="isSider"> Sider </n-layout-sider>
      <n-layout-header class="unvue-header" v-if="isMix || isTop">Header</n-layout-header>
      <n-layout-content class="unvue-content">
        <n-input v-model:value="height"></n-input>
        <n-button @click="setColor">设置header</n-button>
        <br />
        <br />
        <div>布局：{{ layout }}</div>
        <br />
        <n-button @click="layout = 'sider'">左侧菜单模式</n-button>
        <n-button @click="layout = 'mix'">顶部混合模式</n-button>
        <n-button @click="layout = 'top'">顶部菜单模式</n-button>
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
import { computed, ref } from 'vue'
const height = ref(64)
// 布局有：sider（左侧菜单模式），mix（顶部混合模式）top（顶部菜单）
const layout = ref<string>('sider')
const setColor = () => {
  document.documentElement.style.setProperty('--layout-header-height', height.value + 'px')
}
const isSider = computed(() => {
  return layout.value == 'sider'
})
const isMix = computed(() => {
  return layout.value == 'mix'
})
const isTop = computed(() => {
  return layout.value == 'top'
})
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
    background-color: rgb(255, 255, 255);
  }
}
</style>
