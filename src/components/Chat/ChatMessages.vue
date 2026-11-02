<script setup>
import { ref, defineProps, reactive, onMounted, } from 'vue';

defineProps({
    messages:Array
});
for (let i = 0; i < messages.length; i++) {
    console.log(messages[i].text);
}

</script>
<template>
    <div> chatmessages.vue</div>
</template>

<style scoped></style>
