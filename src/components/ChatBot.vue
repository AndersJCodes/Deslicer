<template>
  <div :class="['chat-container', { minimized: isMinimized }]">
    <div class="chat-header" @click="toggleChat"><img src="svg/chat.svg" alt="" /></div>
    <div v-if="!isMinimized" class="chat-body">
      <div class="chat-messages" ref="chatMessages">
        <div
          v-for="(message, index) in messages"
          :key="index"
          class="chat-message"
          :class="{ user: message.isUser }"
        >
          <div v-if="message.image" class="message-with-image">
            <img :src="message.image" alt="GIF response" />
            <p>{{ message.text }}</p>
          </div>
          <p v-else>{{ message.text }}</p>
        </div>
        <div ref="lastMessage"></div>
      </div>

      <form @submit.prevent="askQuestion" class="chat-input">
        <input v-model="question" type="text" placeholder="Ask me a yes/no question..." required />
        <button type="submit">Send</button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watch, nextTick } from 'vue'

interface Messages {
  text: string
  isUser: boolean
  image?: string
}

const question = ref('')
const messages = ref<Messages[]>([])
const chatMessages = ref<HTMLElement | null>(null) // Referens till chat-messages
const isMinimized = ref(true)

const toggleChat = () => {
  isMinimized.value = !isMinimized.value
}

const askQuestion = async () => {
  if (question.value.trim() === '') return

  // Add the user's question
  messages.value.push({ text: question.value, isUser: true })

  try {
    // Fetch response from API
    const response = await fetch('https://yesno.wtf/api')
    const data = await response.json()

    // Add the bot's response
    messages.value.push({
      text: data.answer,
      isUser: false,
      image: data.image,
    })
  } catch (error) {
    // Handle error
    messages.value.push({
      text: 'Oops! Something went wrong. Try again later.',
      isUser: false,
    })
  }

  question.value = '' // Clear the input

  await nextTick()
  scrollToBottom()
}

const scrollToBottom = () => {
  if (chatMessages.value) {
    chatMessages.value.scrollTop = chatMessages.value.scrollHeight
  }
}

watch(messages, () => {
  scrollToBottom()
})
</script>

<style scoped>
/* Chatbot Container */
.chat-container {
  position: fixed;
  bottom: 1rem;
  right: 1rem;
  width: 300px;
  height: 400px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: all 0.3s ease-in-out;
}

.chat-container.minimized {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  overflow: hidden;
}

/* Header */
.chat-header {
  background-color: #f59e0b;
  color: white;
  padding: 1rem;
  cursor: pointer;
  text-align: center;
  border-radius: 8px 8px 0 0;
  transition: background-color 0.3s ease-in-out;
}

.chat-container.minimized .chat-header {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  padding: 0;
  display: flex; /* Använd flexbox för centrering */
  align-items: center;
  justify-content: center;
}

.chat-header:hover {
  background-color: #fbbf24;
}

/* Body */
.chat-body {
  background-color: #ffffff;
  /* padding: 1rem; */
  overflow: hidden;
  border: 1px solid #ddd;
  border-radius: 0 0 8px 8px;
  display: flex;
  flex-direction: column;
  flex: 1;
}

/* Messages */
.chat-messages {
  flex: 1;
  overflow-y: auto;
  padding: 1rem;
  padding-bottom: 4rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.chat-message {
  padding: 0.5rem;
  border-radius: 8px;
  max-width: 70%;
  word-wrap: break-word;
}

.chat-message.user {
  background-color: #fffbeb;
  align-self: flex-end;
}

.chat-message:not(.user) {
  align-self: flex-start;
}

.chat-message img {
  margin-top: 0.5rem;
  max-width: 100%;
  border-radius: 8px;
  position: relative;
}

.message-with-image {
  position: relative;
}

.message-with-image p {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  margin: 0;
  padding: 0.5rem;
  color: white;
  font-weight: bold;
  border-radius: 0 0 8px 8px;
  font-size: 2em;
}

/* Input */
.chat-input {
  display: flex;
  padding: 0.5rem;
  border-top: 1px solid #ddd;
  gap: 0.5rem;
}

.chat-input input {
  flex: 1;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.chat-input button {
  background-color: #f59e0b;
  color: white;
  border: none;
  border-radius: 8px;
  padding: 0.5rem 1rem;
  cursor: pointer;
}

.chat-input button:hover {
  background-color: #fbbf24;
}
</style>
