<template>
  <div class="row conversation-container" 
    v-bind:style="{ display: isVisible}"
    v-bind:class="{ 'hidden': !visible }">
    <div class="col s12 m6 l4 right margin-right-1">
      <div class="card">
        <div class="card-header blue darken-2 conversation-header">
          <i v-on:click="closechat()" class="material-icons right white-text conversation-header-close">close</i>
          <p class="white-text">Widget Chat UI</p>          
        </div>

        <div class="card-content conversation-body">
          <Message user="human" message="Hola Cómo estás"/>
          <Message user="agent" message="Bien ¿Y tú?"/>
          <Message user="human" message="Hola Cómo estás"/>
          <Message user="agent" message="Bien ¿Y tú?"/>
          <Message user="human" message="Hola Cómo estás"/>
          <Message user="agent" message="Bien ¿Y tú?"/>
          <Message user="human" message="Hola Cómo estás"/>
          <Message user="agent" message="Bien ¿Y tú?"/>          
        </div>

        <div class="card-action conversation-footer">
          <button class="btn-floating blue darken-3 waves-effect left dropdown-trigger" data-target='dropdownOptions'><i class="material-icons">add</i></button>
          <ul id='dropdownOptions' class='dropdown-content'>
            <li><a href="#!" class="blue-text darken-1 drop-button"><i class="material-icons center blue-text darken-4">photo</i>Imagen</a></li>
            <li><a href="#!" class="blue-text darken-1 drop-button"><i class="material-icons center blue-text darken-4">description</i>Documento</a></li>
            <li class="divider" tabindex="-1"></li>           
            <li><a href="#!" class="blue-text darken-1 drop-button"><i class="material-icons blue-text darken-4">location_on</i>Ubicación</a></li>
          </ul>
          <div class="input-field col s8 m7 l7 conversation-functions-input-text">
            <input placeholder="Escribe un mensaje..." id="message" type="text" class="validate input-field">          
          </div>      
          <a class="modal-close waves-effect waves-green btn-flat green-text text-darken-2 pointer conversation-send-button">Enviar</a>  
        </div>
        
      </div>
    </div>
  </div>
</template>
<script>
import Message from './Message.vue'
import axios from 'axios'
import { KJUR } from 'jsrsasign'
import configuration from '../configuration'
export default {
  name: 'ChatWindow',
  components:{
    Message
  },
  props: {
    avatar: String,
    visible: Boolean
  },
  watch: { 
    visible: function(newValue){ this.visibility( newValue) }    
  },
  data(){
    return {      
      isVisible: Boolean,
      token: undefined,
      tokenInterval: undefined
    }
  },
  mounted(){
    this.visibility(this.visible)
  },
  created(){
    this.tokenInterval = setInterval(this.generateToken, 3600000)
    this.generateToken()
  },
  methods: {
    visibility(value){
      this.isVisible = (value) ? 'block' : 'none'
    },
    closechat(){      
      this.visibility( false)
      this.$emit('closechat', false)
    },
    generateToken(){
      // Header
      const header = {
        alg: 'RS256',
        typ: 'JWT',
        kid: configuration.private_key_id
      }

      // Payload
      const payload = {
        iss: creds.client_email,
        sub: creds.client_email,
        iat: KJUR.jws.IntDate.get('now'),
        exp: KJUR.jws.IntDate.get('now + 1hour'),
        aud: 'https://dialogflow.googleapis.com/google.cloud.dialogflow.v2.Sessions'
      }
      
      const stringHeader = JSON.stringify(header)
      const stringPayload = JSON.stringify(payload)
      this.token = KJUR.jws.JWS.sign('RS256', stringHeader, stringPayload, creds.private_key)
    }
  }
}
</script>
<style scoped>  
  /*In fact not working transitions :'c */
  .conversation-container {    
    transition-property: visibility, opacity;
    transition-duration: 1s, 1s;
  }
  .conversation-container.hidden{
    opacity: 0;    
    transition-property: opacity, visibility;
    transition-duration: 1s, 0s;
    transition-delay: 0s, 1s;
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
    overflow-x: hidden;
    overflow-y: scroll;
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
  .conversation-send-button{
      display: block!important;
      margin-left: 0;
      padding: 0;
      display: block;
      margin-right: 0px!important;
      font-size: 12px;
  }
</style>


