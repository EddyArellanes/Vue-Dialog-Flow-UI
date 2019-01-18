<template>
  <a class="conversation-floating-button btn-floating btn-large waves-effect waves-light blue darken-2">
    <i class="material-icons">chat</i>
  </a> 
</template>
<script>
export default {
  name: 'FloatingButton',
  props:{
    color: String,
    colorIcon: String,
    icon: String
  }
}
</script>
<style scoped>
  .conversation-floating-button {
    position: fixed;
    top: 88%;
    left: 94%;
  }
  @media only screen and (max-device-width : 768px){    
    .conversation-floating-button {
      position: fixed;
      top: 88%;
      left: 80%;
    }
  }  
</style>


