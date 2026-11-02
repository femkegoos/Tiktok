<script setup>
import { onMounted, ref } from 'vue';
import videoplayer from './components/VideoPlayer/VideoPlayer.vue'
import videodetails from './components/VideoPlayer/VideoDetails.vue'
import chat from './components/Chat/Chat.vue'


let currentVideo = ref("");
let currentDescription = ref("");
let currentUsername = ref("");

let currentIndex = ref(0);
let videos = ref([]);

//onmounted, fetch data from api and log it to console
// api url: https://bit.ly/jsonbintiktok
onMounted(() => {
  fetch('https://api.jsonbin.io/v3/b/670ccbfaad19ca34f8b81951')
    .then(response => response.json())
    .then(data => {
      videos.value = data.record.data.videos;
      currentVideo.value = data.record.data.videos[0].video;
      currentDescription.value = data.record.data.videos[0].description;
      currentUsername.value = data.record.data.videos[0].username;
    })
}); 

function playNext() {
  console.log("play prev video");
  //check index, take the next one, if it is the last one, go back to the first one
  if (currentIndex.value < videos.value.length - 1) {
    currentIndex.value++;
  } else {
    currentIndex.value = 0;
  }
  currentVideo.value = videos.value[currentIndex.value].video;
  currentDescription.value = videos.value[currentIndex.value].description;
  currentUsername.value = videos.value[currentIndex.value].username;
}

function playPrev() {
  console.log("play next video");
  //check index, take the next one, if it is the last one, go back to the first one
  if (currentIndex.value > 0) {
    currentIndex.value--;
  } else {
    currentIndex.value = videos.value.length - 1;
  }
  currentVideo.value = videos.value[currentIndex.value].video;
  currentDescription.value = videos.value[currentIndex.value].description;
  currentUsername.value = videos.value[currentIndex.value].username;
}

</script>
<template>
  <div class="tiktok">
    <div>
      <videoplayer @play-next="playNext" @play-prev="playPrev" :src = "currentVideo"/>
    </div>
    <div>
      <videodetails :description="currentDescription" :username="currentUsername" />
      <chat />
    </div>
  </div>
</template>

<style scoped></style>
