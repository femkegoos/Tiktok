<script setup>
import { ref } from 'vue';

const username = ref('');
const message = ref('');
</script>
<template>
    <div>
        <input type="text" v-model="username" placeholder="Enter your username">
    </div>
    <br>
    <!--commentaar intypen-->
    <div>
    <textarea v-model="message" placeholder="Enter your comment..."></textarea>
    </div>
</template>

<style scoped></style>
