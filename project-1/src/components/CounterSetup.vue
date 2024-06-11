<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0)
const add = () => {
    count.value++
}

</script>

<template>
    <div>{{ count }}</div>
    <button @click="add">add +1</button>
</template>

<style scoped>
</style>
