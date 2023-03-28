<script setup lang="ts">
import { zhCN, dateZhCN } from 'naive-ui'
</script>
<template>
  <n-config-provider :locale="zhCN" :date-locale="dateZhCN">
    <RouterView></RouterView>
    <n-space>
      <a href="#/about">about</a>
      <a href="#">index</a>
    </n-space>
  </n-config-provider>
</template>
