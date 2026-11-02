<script setup>
import { ref } from 'vue';

const username = ref('');
</script>
<template>
    <div>
        <input type="text" v-model="username" placeholder="Enter your username">
    </div>
</template>

<style scoped></style>
