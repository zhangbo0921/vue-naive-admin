<script setup lang="ts">
import { zhCN, dateZhCN } from 'naive-ui'
</script>
<template>
  <n-config-provider :locale="zhCN" :date-locale="dateZhCN">
    <n-button>Hello NaiveUI</n-button>
    <n-input></n-input>
    <n-date-picker type="date" />
  </n-config-provider>
</template>
