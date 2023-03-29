<script setup lang="ts">
import { zhCN, dateZhCN } from 'naive-ui'
</script>
<template>
  <n-config-provider :locale="zhCN" :date-locale="dateZhCN">
    <RouterView></RouterView>
    <n-space>
      <RouterLink to="/">dashboard</RouterLink>
      <RouterLink to="/dashboard/settings">settings</RouterLink>
    </n-space>
  </n-config-provider>
</template>
