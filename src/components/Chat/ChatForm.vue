<script setup>
import { ref } from 'vue';

const username = ref('');
const message = ref('');


function submitMessage() {
    const newMessage = {
        username: username.value,
        text: message.value
    };

    console.log(newMessage);
    fetch('https://chat-api-soulaimane.vercel.app/api/v1/messages', {
        method: 'POST'
    });
}
</script>
<template>
    <form @submit.prevent="submitMessage">
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
