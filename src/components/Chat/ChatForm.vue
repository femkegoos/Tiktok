<script setup>
import { ref } from 'vue';

const username = ref('');
const message = ref('');
</script>
<template>
    <form>
    <div>
        <input type="text" v-model="username" placeholder="Enter your username">
    </div>
    <br>
    <!--commentaar intypen-->
    <div>
    <textarea v-model="message" placeholder="Enter your comment..."></textarea>
    </div>
    <button type="submit">Send comment</button>
    </form>
</template>

<style scoped></style>
