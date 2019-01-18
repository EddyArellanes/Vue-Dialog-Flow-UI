<template>
  <div id="app">
    <FloatingButton v-on:click="openChat()" />
    <ChatWindow/>   
  </div>
</template>

<script>
import FloatingButton from './components/FloatingButton.vue'
import ChatWindow from './components/ChatWindow.vue'

import config from './configuration'

export default {
  name: 'app',
  components: {
    FloatingButton,
    ChatWindow
  },
  data(){
    return {      
      config
    }
  },
  mounted(){

  },
  methods:{
    openChat(){     
      
      let chat = document.querySelector(".conversation-container")
      chat.style.display = "block"    

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
