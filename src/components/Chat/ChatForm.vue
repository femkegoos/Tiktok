<script setup>
import { ref } from 'vue';

const username = ref('');
const message = ref('');
const emit = defineEmits(['message-submitted']);


function submitMessage() {
    const newMessage = {
        user: username.value,
        text: message.value
    };

    console.log(newMessage);
    fetch('https://chat-api-soulaimane.vercel.app/api/v1/messages', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(newMessage)
    })
    .then(response => response.json())
    .then(data => {
       emit('message-submitted', data.data.message);
       username.value = '';
       message.value = '';
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
