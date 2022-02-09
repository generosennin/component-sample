<template>
  <div class="home">
    <input type="text" v-model="message"/><br/>
    <input type="text" v-model="message2"/>
    <HelloWorld v-bind:msg="message" v-on:update="updateMessage"/>
    <HelloWorld :msg="message2" @update="updateMessage2"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src

export default defineComponent({
  name: 'Home',
  components: {
    HelloWorld
  },
  setup () {
    const message = ref<string>()
    message.value = 'hello'
    const message2 = ref<string>()
    message2.value = 'hello hello'

    const updateMessage = (val:string) => {
      message2.value = val
    }
    const updateMessage2 = (val:string) => {
      message.value = val
    }
    return {
      message,
      message2,
      updateMessage,
      updateMessage2
    }
  }
})
</script>
