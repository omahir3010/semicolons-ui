<script>
import { Authenticator } from "@aws-amplify/ui-vue";
import "@aws-amplify/ui-vue/styles.css";
import { Amplify } from "aws-amplify";
import config from "../../src/amplifyconfiguration.json";
import { getCurrentUser } from 'aws-amplify/auth';
import ContentPage from '@/views/ContentPage.vue'
import WelcomePage from '@/views/WelcomePage.vue'
import ChatBot from '@/components/ChatBot.vue'
Amplify.configure(config);

export default{
  components:{
    Authenticator,
    ContentPage,
    ChatBot,
    WelcomePage
  },
  data(){
    return{
      chatBotToggle:false,
    }
  },
  mounted(){
    console.log('Mounted')
    this.currentAuthenticatedUser();
  },
  beforeUpdate(){
    console.log('beforeUpdate')
    this.currentAuthenticatedUser();
  },

  methods:{
    async currentAuthenticatedUser() {
  try {
    const { username, userId, signInDetails } = await getCurrentUser();
    console.log(`The username: ${username}`);
    console.log(`The userId: ${userId}`);
    console.log(signInDetails);
  } catch (err) {
    console.log(err);
  }
},
showChatBot(){
  this.chatBotToggle = true
},
getChatBoxToggleStatus(event){
  console.log(event);
  this.chatBotToggle = event;
}
  }
}
</script>


<template>
  <authenticator>
    <template v-slot="{ user, signOut }">
      <WelcomePage />
      <h1>Hello {{ user.username }}!</h1>
      <button @click="signOut">Sign Out</button>
      <div v-if="chatBotToggle"><ContentPage @emitChatBotToggleEvent="getChatBoxToggleStatus" /></div>
     <div v-if="!chatBotToggle" @click="showChatBot">
      <ChatBot />
     </div>
    </template>
  </authenticator>
</template>

