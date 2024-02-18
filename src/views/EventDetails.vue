<script setup>
import { onMounted, ref } from 'vue'
import EventService from '@/services/EventService'
const event = ref(null)
const props = defineProps({
  id: {
    required: true
  }
})

onMounted(() => {
  EventService.getEvent(props.id)
    .then((response) => {
      event.value = response.data
    })
    .catch((error) => {
      console.error(error)
    })
})
</script>

<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<style>
div {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
