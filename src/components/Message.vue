<template>
  <div>
    <div class="row" v-if="user == 'human'">
      <div class="conversation-bubble conversation-bubble-user">
        <p class="tooltipped" data-position="bottom" data-tooltip="11:57 AM">{{message}}</p>
      </div>
    </div>

    <div class="row" v-else>       
      <img src="../assets/panda-fat.png" class="circle conversation-avatar-size">
      <div class="conversation-bubble conversation-bubble-bot">       
        <p class="tooltipped" data-position="bottom" data-tooltip="12:00 PM">{{message}}</p>
      </div>              
    </div>
  </div>
</template>
<script>
export default {
  name: 'Message',
  props:{
    user: String, //human || agent
    message: String
  },
  data(){
    return {

    }
  }
}
</script>
<style scoped>
  .conversation-bubble{  
    display: block;   
    border-radius: 16px;
    color: black;
    padding: 8px;
  }
  .conversation-bubble{
    display: block;
  }
  .conversation-bubble-user{
    background-color: #1976D2;
    color: white;
    float: right;
  }
  .conversation-avatar-size{
    width: 60px;
    margin-right: 4px;
    float: left;
  }   
  .conversation-bubble-bot{
    background-color: #f4f4f4;
    float: left;
  }  
</style>

