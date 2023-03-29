<template>
  <div>
    {{ title }}
    <n-button @click="click">{{ counter.count }}</n-button>
  </div>
</template>
<script setup lang="ts">
import { useCounterStore } from '@/stores'
const counter = useCounterStore()

const click = () => {
  counter.increment()
}
const title = 'dashboard page'
</script>
