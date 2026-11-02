<script setup>
import{ ref, defineProps, reactive, onMounted,} from 'vue';
import chatmessages from './ChatMessages.vue';
import chatForm from './ChatForm.vue';

const messages = ref([]);


//api https://chat-api-soulaimane.vercel.app/api/v1/messages
onMounted(() => {
  fetch('https://chat-api-soulaimane.vercel.app/api/v1/messages')
    .then(response => response.json())
    .then(data => {
      messages.value = data.data.messages[0].text;
    })
}); 
</script>
<template>
<div>
    <chatmessages />
    <chatForm />
</div>>
</template>

<style scoped>
div{
    padding: 32px;
}
</style>



