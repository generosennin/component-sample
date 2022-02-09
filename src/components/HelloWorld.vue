<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>ここはhello world</p>
    <input type="text" v-model="message3"/>
    <button @click="send">send</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String
  },
  setup (props, context) {
    const message3 = ref<string>()
    message3.value = props.msg

    const send = () => {
      context.emit('update', message3.value)
    }
    return {
      message3,
      send
    }
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
