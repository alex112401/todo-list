
<template>
  <div class="container mx-auto">  
    <Navbar />
    <div class="flex">
      <input v-model="eventName" type="text" placeholder="new event" class="input input-bordered w-full max-w-xs mr-1" />
      <button class="btn btn-outline" @click="addEvent">add new event</button>
    </div>
    <event @remove-event="removeEvent" v-for="event in eventList" :event="event"/>
  </div>
</template>

<script setup>
import Navbar from './Navbar.vue'
import event from '../block/event.vue'
import { v4 as uuid } from "uuid"
import { reactive, ref } from 'vue'

const eventList = reactive([])
const eventName = ref("")

function addEvent() {
  const eventObj = {
    name: eventName.value,
    id: uuid()
  }
  eventList.push(eventObj)
}

function removeEvent(id){
  const index = eventList.findIndex((event) => event.id == id)
  eventList.splice(index, 1)
}

</script>


<style scoped>

</style>
