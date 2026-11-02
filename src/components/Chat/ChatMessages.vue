<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    messages: Array
});
</script>
<template>
    <div>
        <h2>Comments</h2>
        <div v-for="message in props.messages">
            <p>{{ message.user || message.username }}</p>
            <p>{{ message.text }}</p>   

        </div>
        <p>Chat component werkt!</p>
        <p>Aantal berichten: {{ props.messages.length }}</p>
    </div>
</template>

<style scoped></style>
