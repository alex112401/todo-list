<template>
  <div class="container flex my-5 bg-yellow-400 justify-between items-center">
    <div class="flex">
      <input type="checkbox" v-model="check" class="checkbox mx-3" />
      <div :class="`${check ? 'line-through' : ''}`" >{{event.name}} </div>
    </div>
    <button class="btn btn-square btn-outline" @click="deleteEvent">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" /></svg>
    </button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue"
import { reactive, ref } from 'vue'

const emits = defineEmits(["remove-event"])


const props = defineProps({
  event: {
    type: Object,
    required: true,
  },
})

const check = ref(false)

function deleteEvent(){
  emits("remove-event", props.event.id)
}

</script>