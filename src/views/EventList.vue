<script setup>
// import axios from 'axios' no longer neede
import EventService from '@/services/EventService.js'
import EventCard from '@/components/EventCard.vue'
import { ref, onMounted } from 'vue'
const events = ref(null)
onMounted(() => {
  // axios
  //   .get('https://my-json-server.typicode.com/LiyanKhanduqji/Axois/events')
  EventService.getEvents()
    .then((response) => {
      events.value = response.data
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <event-card v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: monospace;
}
</style>
