<script setup>
//https://vue-3-tiktok.vercel.app/video1.mp4
import{ ref, defineProps, reactive, onMounted } from 'vue';
import "animate.css";

const props = defineProps({
    src: {
        type: String,
        required: true
    }
    
});
const emit = defineEmits(['playPrev', 'playNext']);



</script>
<template>
<div>
    <Transition
    mode="out-in"
    enter-active-class="animate__animated animate__fadeIn"
    leave-active-class="animate__animated animate__fadeOut">
        <video :key="props.src" :src="props.src" autoplay muted loop></video>
    </Transition>
    <div class="controls">
        <a @click.prevent="$emit('playPrev')" href="#">&#x2191;</a>
        <a @click.prevent="$emit('playNext')" href="#">&#x2193;</a>
    </div>
</div>
</template>

<style scoped>
video{
    width: 100%;
    height: 100%;
    object-fit: cover;
    position: relative;
    border-radius: 16px;
    margin: 16px;
}
.controls{
    position: absolute;
    bottom: 320px;
    left: 10px;
    z-index: 10;
    display: flex;
    flex-direction: column;
    gap: 40px;
    font-size: 72px;
    font-weight: bold;
}
.controls a{
    color: white;
    text-decoration: none;
    margin-left: 16px;
}

</style>



