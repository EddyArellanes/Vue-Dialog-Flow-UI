<template>
  <div class="row conversation-container">
    <div class="col s12 m6 l4 right margin-right-1">
      <div class="card">
        <div class="card-header blue darken-2 conversation-header">
          <i onclick="closeChat()" class="material-icons right white-text conversation-header-close">close</i>
          <p class="white-text">Widget Chat UI</p>          
        </div>

        <div class="card-content conversation-body">
          <div class="row">
            <div class="conversation-bubble conversation-bubble-user">
              <p class="tooltipped" data-position="bottom" data-tooltip="11:57 AM">Hola Cómo estás</p>
            </div>
          </div>
          <div class="row">       
            <img src="../assets/panda-fat.png" class="circle conversation-avatar-size">
            <div class="conversation-bubble conversation-bubble-bot">       
              <p class="tooltipped" data-position="bottom" data-tooltip="12:00 PM">Bien ¿Y tú?</p>
            </div>              
          </div>
        </div>

        <div class="card-action conversation-footer">
          <button class="btn-floating blue darken-3 waves-effect left dropdown-trigger" data-target='dropdownOptions'><i class="material-icons">add</i></button>
          <ul id='dropdownOptions' class='dropdown-content'>
            <li><a href="#!" class="blue-text darken-1 drop-button"><i class="material-icons center blue-text darken-4">photo</i>Imagen</a></li>
            <li><a href="#!" class="blue-text darken-1 drop-button"><i class="material-icons center blue-text darken-4">description</i>Documento</a></li>
            <li class="divider" tabindex="-1"></li>           
            <li><a href="#!" class="blue-text darken-1 drop-button"><i class="material-icons blue-text darken-4">location_on</i>Ubicación</a></li>
          </ul>
          <div class="input-field col s7 m7 l7 conversation-functions-input-text">
            <input placeholder="Escribe un mensaje..." id="message" type="text" class="validate input-field">          
          </div>      
          <a class="modal-close waves-effect waves-green btn-flat green-text text-darken-2 pointer">Enviar</a>  
        </div>
        
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'ChatWindow',
  props: {
    avatar: String,
    visible: Boolean
  }
}
</script>
<style scoped>  
  .conversation-container {
    -webkit-animation: shadow-drop-center 0.4s cubic-bezier(0.250, 0.460, 0.450, 0.940) both;
    animation: shadow-drop-center 0.4s cubic-bezier(0.250, 0.460, 0.450, 0.940) both;
  }
  .conversation-container{
    margin-top: 2%;
  }
  .conversation-header{
    height: 48px;
  }
  .conversation-header-close{
    padding-top: 32px;
    padding-right: 0;    
  }
  .conversation-header-close{
    padding-top: 16px;
    padding-right: 16px;
  }
  .conversation-header-close:hover{
    cursor: pointer;
  }	 
  .conversation-header > p{
    color: white;
    display: inline-block;      
    margin-left: 24px;
  }
  .conversation-body{
    height: 400px;
  }
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
  .conversation-footer{
      height: 100px;
  }
  .drop-button{
    text-transform: initial!important;
  }
  .conversation-functions-input-text{
    margin-top: -1%;
    height: 2.3rem;
  }
</style>


