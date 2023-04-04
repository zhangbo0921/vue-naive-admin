<template>
  <n-layout
    class="unvue-pro-layout"
    :has-sider="isSider"
    :position="(isSider && fixedSider) || (isMix && fixedHeader) ? 'absolute' : 'static'"
  >
    <n-layout-header
      class="unvue-header"
      bordered
      v-if="isMix || isTop"
      :style="isMix && fixedHeader ? { height: headerHeight + 'px' } : {}"
      >Header</n-layout-header
    >
    <n-layout-sider
      v-if="isSider"
      class="unvue-sider"
      bordered
      inverted
      :collapsed-width="siderbarCollapsedWidth"
      :width="siderbarWidth"
      :show-trigger="siderbarShowTrigger ? 'bar' : false"
      :native-scrollbar="false"
      :style="{ minHeight: '100vh' }"
    >
      <div>Sider</div>
    </n-layout-sider>
    <n-layout
      :has-sider="isMix"
      :position="isMix && fixedHeader ? 'absolute' : 'static'"
      :style="isMix && fixedHeader ? { top: headerHeight + 'px' } : {}"
    >
      <n-layout-sider
        v-if="isMix"
        class="unvue-sider"
        bordered
        inverted
        :collapsed-width="siderbarCollapsedWidth"
        :width="siderbarWidth"
        :show-trigger="siderbarShowTrigger ? 'bar' : false"
        :native-scrollbar="false"
      >
        <div>Sider0</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider</div>
        <div>Sider1</div>
      </n-layout-sider>
      <n-layout-header
        v-if="isSider"
        class="unvue-header"
        bordered
        :position="isSider && fixedHeader ? 'absolute' : 'static'"
      >
        Header
      </n-layout-header>
      <n-layout-content
        class="unvue-content"
        :native-scrollbar="false"
        :position="isSider && fixedHeader ? 'absolute' : 'static'"
        :style="{ top: isSider && fixedHeader ? headerHeight + 'px' : '' }"
      >
        <n-input v-model:value="headerHeight"></n-input>
        <n-button @click="setColor">设置header</n-button>
        <br />
        <br />
        <div>布局：{{ layout }}</div>
        <br />
        <n-button @click="layout = 'sider'">左侧菜单模式</n-button>
        <n-button @click="layout = 'mix'">顶部混合模式</n-button>
        <n-button @click="layout = 'top'">顶部菜单模式</n-button>
        <br />
        <n-switch v-model:value="fixedSider" size="small" :disabled="!enableFixedSider">
          <template #checked>固定Sider</template>
          <template #unchecked>不固定Sider</template>
        </n-switch>
        <n-switch v-model:value="fixedHeader" size="small" :disabled="!enableFixedHeader">
          <template #checked>固定header</template>
          <template #unchecked>不固定header</template>
        </n-switch>
        <n-space>
          <RouterLink to="/">dashboard</RouterLink>
          <RouterLink to="/dashboard/settings">settings</RouterLink>
        </n-space>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈1</div>
        <div>test1哈哈2</div>
        <RouterView></RouterView>
      </n-layout-content>
    </n-layout>
  </n-layout>
</template>
<script setup lang="ts">
import { computed, ref, watchEffect } from 'vue'
const headerHeight = ref('64')
const siderbarWidth = ref(200)
const siderbarCollapsedWidth = ref(60)
const siderbarShowTrigger = ref<boolean>(true)
const fixedSider = ref<boolean>(false)
const fixedHeader = ref<boolean>(false)
const enableFixedSider = ref<boolean>(true)
const enableFixedHeader = ref<boolean>(true)

// 布局有：sider（左侧菜单模式），mix（顶部混合模式）top（顶部菜单）
const layout = ref<string>('sider')
const setColor = () => {
  document.documentElement.style.setProperty('--layout-header-height', headerHeight.value + 'px')
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
watchEffect(() => {
  if (isSider.value) {
    enableFixedHeader.value = true
    if (fixedHeader.value) {
      fixedSider.value = true
      enableFixedSider.value = false
    } else {
      enableFixedSider.value = true
    }
  }
  if (isMix.value) {
    fixedSider.value = false
    enableFixedHeader.value = true
    enableFixedSider.value = false
  }
  if (isTop.value) {
    enableFixedSider.value = false
    enableFixedHeader.value = false
    fixedSider.value = false
    fixedHeader.value = false
  }
})
</script>
<style lang="less">
@import url('@/less/var.less');
.unvue-pro-layout {
  min-height: 100vh;
  .unvue-header {
    height: @layout-header-height;
    z-index: 11;
  }
  .unvue-sider {
    min-height: calc(100vh - @layout-header-height);
  }
  .unvue-content {
    padding: 4px;
    background-color: rgb(255, 255, 255);
  }
}
</style>
