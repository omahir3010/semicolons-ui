
<template>
    <div class="chatbox-container">
<div class="container">
  <h1 class="bot-header">Ai Chat Bot   <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" height="25px" width="25px" style="margin-top: 6px;" @click="emitEvent">
  <path d="M6.28 5.22a.75.75 0 0 0-1.06 1.06L8.94 10l-3.72 3.72a.75.75 0 1 0 1.06 1.06L10 11.06l3.72 3.72a.75.75 0 1 0 1.06-1.06L11.06 10l3.72-3.72a.75.75 0 0 0-1.06-1.06L10 8.94 6.28 5.22Z" />
</svg></h1>

<div class="messageBox mt-8">
  <template v-for="(message, index) in messages" :key="index">
    <div :class="message.from == 'user' ? 'messageFromUser' : 'messageFromChatGpt'">
      <div :class="message.from == 'user' ? 'userMessageWrapper' : 'chatGptMessageWrapper'">
        <div :class="message.from == 'user' ? 'userMessageContent' : 'chatGptMessageContent'">{{ message.data }}</div>
      </div>
    </div>
  </template>
</div>
<div class="inputContainer">
  <input
    v-model="currentMessage"
    type="text"
    class="messageInput"
    placeholder="Ask me anything..."
  />
  <button
    @click="sendMessage(currentMessage)"
    class="askButton"
  >
    Ask
  </button>
</div>
</div>
</div>
</template>

<script>
export default {
     /* eslint-disable */
  name: 'ChatBox',
  data() {
    return {
      currentMessage: '',
      messages: [],
    };
  },
  methods: {
    async sendMessage(message) {
      this.messages.push({
        from: 'user',
        data: message,
      });
      await axios
        .post('http://localhost:3000/chatbot', {
          message: message,
        })
       .then((response) => {
  this.messages.push({
    from: 'chatGpt',
    data: response.data.data, // Access the 'data' property of the response object
  });
});

    },
    emitEvent(){
            console.log('E E')
            this.$emit('emitChatBotToggleEvent', false)
        }
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap');

.chatbox-container {
  position: fixed;
  bottom: 24px;
  right: 24px;
  z-index: 1000;
}

.container {
  width: 300px;
  height: 500px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  overflow: hidden;
  font-family: 'Roboto', sans-serif;
}

h1 {
  font-size: 24px;
  font-weight: 500;
  text-align: center;
  color: #222;
  padding: 16px;
  margin: 0;
  background-color: #f7f7f7;
  border-bottom: 1px solid #e7e7e7;
}

.messageBox {
  padding: 16px;
  flex-grow: 1;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.messageFromUser,
.messageFromChatGpt {
  display: flex; }



.messageBox {
  max-height: 400px;
  overflow-y: auto;
  padding: 0 16px;
  border-top: 1px solid #f0f0f0;
  border-bottom: 1px solid #f0f0f0;
  flex-grow: 1;
}

.messageFromUser,
.messageFromChatGpt {
  display: flex;
  margin-bottom: 8px;
}

.userMessageWrapper,
.chatGptMessageWrapper {
  display: flex;
  flex-direction: column;
}

.userMessageWrapper {
  align-self: flex-end;
}

.chatGptMessageWrapper {
  align-self: flex-start;
}

.userMessageContent,
.chatGptMessageContent {
  max-width: 100%;
  padding: 8px 12px;
  border-radius: 18px;
  margin-bottom: 2px;
  font-size: 14px;
  line-height: 1.4;
}

.userMessageContent {
  background-color: #1877F2;
  color: white;
  border-top-left-radius: 0;
}

.chatGptMessageContent {
  background-color: #EDEDED;
  color: #222;
  border-top-right-radius: 0;
}

.userMessageTimestamp,
.chatGptMessageTimestamp {
  font-size: 10px;
  color: #999;
  margin-top: 2px;
}

.userMessageTimestamp {
  align-self: flex-end;
}

.chatGptMessageTimestamp {
  align-self: flex-start;
}

.inputContainer {
  display: flex;
  align-items: center;
  padding: 8px;
  background-color: #f0f0f0;
}

.messageInput {
  flex-grow: 1;
  border: none;
  outline: none;
  padding: 12px;
  font-size: 16px;
  background-color: white;
  border-radius: 24px;
  margin-right: 8px;
}

.askButton {
  background-color: #1877F2;
  color: white;
  font-size: 16px;
  padding: 8px 16px;
  border: none;
  outline: none;
  cursor: pointer;
  border-radius: 24px;
  transition: background-color 0.3s ease-in-out;
}

.askButton:hover {
  background-color: #145CB3;
}
.bot-header{
    display: flex;
    justify-content: space-evenly;
}

@media (max-width: 480px) {
  .container {
    width: 100%;
    max-width: none;
    border-radius: 0;
  }
}
.chatbox-container {
  position: fixed;
  bottom: 24px;
  right: 24px;
  z-index: 1000;
}


.messageBox {
  padding: 16px;
  flex-grow: 1;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.messageFromUser,
.messageFromChatGpt {
  display: flex;
}
</style>