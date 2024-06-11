<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
    name: 'Counter',
    data() {
        return {
            count: 0
        }
    },
    mounted() {
        console.log(this.count)

        this.count = 1
    },
    methods: {
        add() {
            this.count++
        }
    },
})

</script>

<template>
    <div>{{ count }}</div>
    <button @click="add">add 1</button>
</template>

<style scoped>
</style>