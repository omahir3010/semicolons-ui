<template>
    <body class="bg-yellow-300">
        <header class="py-4">
            <div class="container mx-auto flex justify-between items-center px-6">
                <div class="text-white">
                    <a href="#" class="text-xl text-black font-semibold">Persistent Semicolons</a>
                </div>
                <nav class="flex space-x-4">
                    <!-- <a href="#" class="text-white bg-black w-[120px] h-[40px] pt-[8px] font-semibold">Chapters</a> -->
                    <!-- <a href="#" class="text-black font-semibold"></a>
                    <a href="#" class="text-black font-semibold">Course</a> -->
                    <a href="#" class="text-white bg-black w-[100px] h-[40px] pt-[8px] font-semibold rounded-3xl"
                        v-if="!getSignedInState" @click="openAuth()">Log In</a>
                    <a href="#" class="text-white bg-black w-[100px] h-[40px] pt-[8px] font-semibold rounded-3xl"
                        v-if="getSignedInState" @click="handleSignOut">Log Out</a>

                </nav>
            </div>
        </header>
        <main class="py-10">
            <div class="container mx-auto px-6 flex">
                <div class="mt-12">
                    <h1 class="text-[30px] font-bold text-black mb-4" id="title">AI Scholar's</h1>
                    <p class="text-xl text-black mb-8">Speed Up The Skill Acquisition Process By Finding Unlimited Courses
                        That
                        Matches Your Niche.</p>
                    <div class="flex" v-if="getSignedInState">
                        <div class=" ml-[43px] border-[2px] shadow-2xl border-black w-[180px] h-[220px]">
                            <div class="card ">
                                <div>
                                   <h2 class="mt-6 font-semibold text-[28px]">
                                    Text Generation
                                   </h2>
                                </div>
                                <button class="text-white bg-black w-[100px] h-[40px] font-semibold rounded-3xl mt-[30px]" @click="visibleTextGeneration = true" >Show</button>
                                <Dialog v-model:visible="visibleTextGeneration" modal header="Text Generation" :style="{ width: '50rem' }"
                                    :breakpoints="{ '1199px': '75vw', '575px': '90vw' }">
                                    <p class="mb-5">
                                        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
                                        incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud
                                        exercitation ullamco laboris nisi ut aliquip ex ea commodo
                                        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum
                                        dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident,
                                        sunt in culpa qui officia deserunt mollit anim id est laborum.
                                    </p>
                                    <p class="mb-5">
                                        "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium
                                        doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore
                                        veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim
                                        ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia
                                        consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro
                                        quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur,
                                        adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore
                                        magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum
                                        exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid
                                        ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate
                                        velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo
                                        voluptas nulla pariatur?
                                    </p>

                                </Dialog>
                            </div>
                        </div>
                        <div class=" border-[2px] shadow-2xl border-black w-[180px] h-[220px] ml-[40px]">
                            <div class="card ">
                                <div>
                                   <h2 class="mt-6 font-semibold text-[28px]">
                                    Notes Generation
                                   </h2>
                                </div>
                                <button class="text-white bg-black w-[100px] h-[40px] font-semibold rounded-3xl mt-[30px]" @click="visibleNotesGeneration = true" >Show</button>
                                <Dialog v-model:visible="visibleNotesGeneration" modal header="Notes Generation" :style="{ width: '50rem' }"
                                    :breakpoints="{ '1199px': '75vw', '575px': '90vw' }">
                                    <p class="mb-5">
                                        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
                                        incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud
                                        exercitation ullamco laboris nisi ut aliquip ex ea commodo
                                        consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum
                                        dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident,
                                        sunt in culpa qui officia deserunt mollit anim id est laborum.
                                    </p>
                                    <p class="mb-5">
                                        "Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium
                                        doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore
                                        veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim
                                        ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia
                                        consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro
                                        quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur,
                                        adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore
                                        magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum
                                        exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid
                                        ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate
                                        velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo
                                        voluptas nulla pariatur?
                                    </p>

                                </Dialog>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="mt-10 flex justify-center">
                    <img src="../assets/studying.png"
                        alt="Illustration of people engaging in different learning activities, such as reading, using computers, and painting, to represent the variety of courses available.">
                </div>
            </div>
            <div v-if="getSignedInState" @click="showChatBot">
                <ChatBot />
            </div>
            <div class="chatbox-container" v-if="getSignedInState && chatBotToggle">
                <div class="container1">
                    <h1 class="bot-header">Ai Chat Bot <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"
                            fill="currentColor" height="25px" width="25px" style="margin-top: 6px;" @click="emitEvent">
                            <path
                                d="M6.28 5.22a.75.75 0 0 0-1.06 1.06L8.94 10l-3.72 3.72a.75.75 0 1 0 1.06 1.06L10 11.06l3.72 3.72a.75.75 0 1 0 1.06-1.06L11.06 10l3.72-3.72a.75.75 0 0 0-1.06-1.06L10 8.94 6.28 5.22Z" />
                        </svg></h1>

                    <div class="messageBox mt-8">
                        <template v-for="message in getMessagesArr" :key="message.id">
                            <div class="userMessageContent" v-if="message.from.type === 'user'">
                                {{ message.msg.message }}
                            </div>
                            <div class="chatGptMessageContent" v-if="message.from.type === 'gpt'">
                                {{ message.msg.message }}
                            </div>
                        </template>
                    </div>
                    <div class="inputContainer">
                        <input v-model="currentMessage" type="text" class="messageInput" placeholder="Ask me anything..." />
                        <button @click="sendMessage(currentMessage)" class="askButton">
                            Ask
                        </button>
                    </div>
                </div>
            </div>
            <div>

            </div>
        </main>
        <footer class="py-6">
            <div class="container mx-auto px-6">
                <p class="text-black text-center">© 2024 MÖNAC. All rights reserved.</p>
            </div>
        </footer>
    </body>
</template>

<script>
import { signOut } from 'aws-amplify/auth';
import ChatBot from '@/components/ChatBot.vue';
import axios from 'axios';
import Dialog from 'primevue/dialog';

export default {
    components: {
        ChatBot,
        Dialog
    },
    data() {
        return {
            currentMessage: '',
            messages: [],
            getMessagesArr: [],
            chatBotToggle: false,
            visibleTextGeneration: false,
            visibleNotesGeneration: false

        }
    },
    computed: {
        getSignedInState() {
            if (localStorage.getItem('signedIn') === 'signedIn') {
                return true;
            }
            else {
                return false;
            }
        }
    },
    mounted() {
        this.getMessages();
    },
    methods: {
        openAuth() {
            localStorage.setItem('authState', true);
            location.reload();
        },
        showChatBot() {
            this.chatBotToggle = true
        },

        async handleSignOut() {
            try {
                await signOut();
                location.reload();
            } catch (error) {
                console.log('error signing out: ', error);
            }
        },
        async getMessages() {
            await axios.get('http://localhost:3000/chat').then((response) => {
                this.getMessagesArr = response.data;
                console.log(this.getMessagesArr);

            }).catch((err) => {
                console.log('Caught an Error: ', err)
            })
        },
        async sendMessage(message) {
            let msgArr = {
                "from": {
                    "type": "gpt"
                },
                "msg": {
                    "message": message

                }
            }
            this.getMessagesArr.push(msgArr);
            await axios
                .post('http://localhost:3000/chat', msgArr)
                .then((response) => {
                    console.log(response);

                });

        },
        emitEvent() {
            this.chatBotToggle = false
        }

    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Cedarville+Cursive&display=swap');

.chatbox-container {
    position: fixed;
    bottom: 24px;
    right: 24px;
    z-index: 1000;
}

@font-face {
    font-family: 'google-cursive';
    src: url('https://fonts.googleapis.com/css2?family=Cedarville+Cursive&display=swap');
}

#title {
    font-family: 'google-cursive';
}

.container1 {
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
    max-width: 70%;
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
    margin-right: 30px;
}

.chatGptMessageContent {
    background-color: #EDEDED;
    color: #222;
    border-top-right-radius: 0;
    margin-left: 30%;
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

.bot-header {
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
}</style>