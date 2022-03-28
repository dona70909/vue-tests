<template>
  <div id="app">
    <section class="position-relative">
      <section class="my-top-background">

      </section>

      <section class="container-fluid my-main-content-position position-absolute">
        <div class="row justify-content-center">
          <div class="col-12 my-main-content-wrapper d-flex justify-content-center">
            <!-- // #############  #lEFT ############## -->
            <div class="col-4 d-flex flex-column my-main-content-left">
              <!-- // % First contact -->
              <div class="my-contact-wrapper my-selected-contact-wrapper selected-gray d-flex justify-content-between px-2 py-3">
                <div class="my-contact-left d-flex">
                  <div class="my-pic-bg me-2">
                      <img :src="profilePic" alt="foto">

                  </div>
                  <h5 class="contact-name">Sofia</h5>
                </div>
                                
                <div class="my-contact-right">
                    <i class="bi bi-arrow-clockwise fs-4 icon-grey"></i>
                    <i class="bi bi-chat-left-fill fs-4 icon-grey"></i>
                    <i class="bi bi-three-dots-vertical fs-4 icon-grey"></i>
                </div>
              </div>  

              <!-- / %Alert -->
              <div class="my-message-alert-wrapper selected d-flex">
                <div class="bell-icon-bg me-2">
                    <i class="bi bi-bell-slash-fill"></i>
                </div>
                <div class="text-alert-wrap">
                    <p class="m-0 my-alert">Ricevi notifiche di nuovi messaggi</p>
                    <p class="m-0 my-alert-active-msg"><a href="#/">Attiva notifiche</a></p>
                </div>
              </div>
              <!-- // % search -->
                <div class="my-search-box-wrapper d-flex">
                  <i class="bi bi-search icon-grey"></i>
                  <input v-model="inputContact" type="search" placeholder="Search" class="my-search-bar">
                </div>
                <ListContact/>
            </div>  



          <!-- //! #############   RIGHT ############## -->
            <div class="col-6 my-main-content-right d-flex flex-column justify-content-between">
              <SelectedContact/>
              
            </div>  
          </div> 
        </div>  
      </section>  
    </section>
  </div>
</template>

<script>
import ListContact from "./components/ListContact.vue"
import SelectedContact from "./components/SelectedContact.vue"

export default {
  name: 'App',
  components: {
    ListContact,
    SelectedContact,
  },

  data(){
    return{
      contacts : [
        {
          name: 'Michele',
          avatar: '_1',
          visible: true,
          messages: [
            {
              date: '10/01/2020 15:30:55',
              message: 'Hai portato a spasso il cane?',
              status: 'sent'
            },
            {
              date: '10/01/2020 15:50:00',
              message: 'Ricordati di stendere i panni',
              status: 'sent'
            },
            {
              date: '10/01/2020 16:15:22',
              message: 'Tutto fatto!',
              status: 'received'
            }
          ],
          
          image:require('@/assets/img/avatar_1.jpg'),
        },
        {
          name: 'Fabio',
          avatar: '_2',
          visible: true,
          messages: [
            {
              date: '20/03/2020 16:30:00',
              message: 'Ciao come stai?',
              status: 'sent'
            },
            {
              date: '20/03/2020 16:30:55',
              message: 'Bene grazie! Stasera ci vediamo?',
              status: 'received'
            },
            {
              date: '20/03/2020 16:35:00',
              message: 'Mi piacerebbe ma devo andare a fare la spesa.',
              status: 'sent'
            },
            {
              name: 'Claudia',
              avatar: '_6',
              visible: true,
              messages: [
                {
                  date: '10/01/2020 15:30:55',
                  message: 'Ciao Claudia, hai novità?',
                  status: 'sent'
                },
                {
                  date: '10/01/2020 15:50:00',
                  message: 'Non ancora',
                  status: 'received'
                },
                {
                  date: '10/01/2020 15:51:00',
                  message: 'Nessuna nuova, buona nuova',
                  status: 'sent'
                }
              ],
              
              image:require('@/assets/img/avatar_6.jpg'),
                
            },
          ],
          
          
        }
    
      ],

      activeClick:null,
      inputMessage:"",
      inputContact:"",
      activeMessage:null,
      profilePic:require('./assets/img/avatar_io.jpg'),
      
    
    }
    


  },

  methods: {
    getActiveClick(index){
      this.activeClick = index;
    },
    getActiveMessage(index){
      this.activeMessage = index;
    },
    
    pushMessage(pushElement){
      this.contacts.forEach((contact,index) => {
        if(this.activeClick == index){
          this.contacts[this.activeClick].messages.push(pushElement);
          console.log("active" +  this.contacts[this.activeClick].messages );
        }else {
          console.log("not active, no push");
        }
      });
    },

    removeMessage(indexMsg){
      this.contacts.forEach((contact,index) => {
        if((this.activeClick == index) && (this.activeMessage == indexMsg)){
            this.contacts[this.activeClick].messages.splice(this.activeMessage,1);
            console.log("active" + " " + this.activeClick + " " + index);
        }else {
            console.log("not active, no remove");
        }
      });
    },

    /* getInput(input){
      if(input != ""){
          newMessage = this.createNewMessage();
          newAnswer = this.createNewAnswer();
          this.pushMessage(newMessage);
          setTimeout(this.timeFn,3000);
          newMessage.message = input;
          this.inputMessage = "";
      } else {
          console.log("empty msg");
      }
    }, */
    
    createNewMessage(){
      const today = new Date();
      return {
          date:today.getDate()+'/'+(today.getMonth()+1)+'/'+today.getFullYear() + ' ' +
          today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds(),
          message:"",
          status:"sent"
      }
    },
    
    createNewAnswer(){
      const today = new Date();
      return {
          date:today.getDate()+'/'+(today.getMonth()+1)+'/'+today.getFullYear() + ' ' +
          today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds(),
          message:"ok",
          status:"received"
      }
    },
        
  /*  timeFn(){
        this.pushMessage(newAnswer);
    }, */

    computed: {
      checkSearchContact(){
          this.activeClick = 0;
          return this.contacts.filter(contact => {
              return contact.name.toLowerCase().includes(this.inputContact.toLowerCase());
          });
      }
    },
  },
}
</script>

<style lang="scss">

</style>
