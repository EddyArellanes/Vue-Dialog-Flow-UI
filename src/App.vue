<template>
  <div id="app">
    <FloatingButton @openchat="config.chatWindow.visibleOnStart = true" />
    <ChatWindow 
    @closechat="config.chatWindow.visibleOnStart = false" 
    :visible="config.chatWindow.visibleOnStart"/>   
  </div>
</template>

<script>
import FloatingButton from './components/FloatingButton.vue'
import ChatWindow from './components/ChatWindow.vue'

import { configuration} from './configuration'


export default {
  name: 'app',
  components: {
    FloatingButton,
    ChatWindow
  },
  data(){
    return {      
      config: configuration
    }
  },
  mounted(){    
  },
  methods:{
    
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
