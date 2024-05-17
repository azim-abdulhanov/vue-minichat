<template>
  <section class="chat">
    <div class="chat-user">
      <ChatTop img="alex" name="Александр"/>
      <ChatMain sender="1" :messages="messages"/>
      <ChatButton sender="1" @message="sendMessage"/>
    </div>

    <div class="chat-user">
      <ChatTop img="evgen" name="Евгений"/>
      <ChatMain sender="2" :messages="messages"/>
      <ChatButton sender="2" @message="sendMessage"/>
    </div>
  </section>
</template>

<script>
import ChatTop from './components/ChatTop.vue'
import ChatMain from './components/ChatMain.vue'
import ChatButton from './components/ChatButton.vue'

export default {
  components: {
    ChatTop,
    ChatButton,
    ChatMain
  },
  data() {
    return {
      messages: [],
    }
  },
  methods: {
    sendMessage(message) {
      this.messages.push(message)
      localStorage.message = JSON.stringify(this.messages)
    }
  },
  created() {
    const message = localStorage.message ? JSON.parse(localStorage.message) : []
    this.messages = message
  },
}
</script>

<style scoped>
.chat {
  display: flex;
  gap: 20px;
}

.chat-user {
  display: flex;
  flex-direction: column;
  width: 400px;
  height: 100%;
  background: url(@/assets/img/bg.png);
  overflow: hidden;
  border-radius: 10px;
}
@media (max-width: 1024px) {
  .chat {
    display: flex;
  }
}
@media (max-width: 800px) {
  .chat {
    display: flex;
    gap: 10px;
  }
  .chat-user {
    max-width: 300px;
  }
}
@media (max-width: 600px) {
  .chat {
    flex-direction: column;
  }
}
@media (max-width: 500px) {
  .chat {
    flex-direction: column;
    gap: 5px;
  }
  .chat-user {
    max-width: 300px;
  }
}

@media (max-width: 320px) {
  .chat-user {
    max-width: 250px;
    height: 100%;
  }

}
</style>
