<template>
  <div>
    <form class="chat-button">
      <input
        type="text"
        placeholder="Написать сообщение..."
        v-model="message"
      >
      <button
        v-if="message.length"
        @click="sentMessage"
      >
        <img src="../assets/img/arrow.svg" alt="">
      </button>
      <button
        v-else
        @click.prevent="sentMessage,
        btn = !btn"
      >
        <img src="../assets/img/kamera.svg" alt="">
      </button>
    </form>

    <div class="chat-modal" v-if="btn">
      <div class="chat-modal-wrap">
        <div class="chat-modal-title">
          Отправить картинку
        </div>
        <form class="chat-modal-form">
          <input
            class="chat-modal-form-file"
            type="text"
            v-model="url"
            placeholder="URL"
          >
          <input
            class="chat-modal-form-text"
            type="text"
            v-model="messageBtn"
            placeholder="Комментарий"
          >
          <div class="chat-modal-btns">
            <button class="chat-modal-btn-send" @click="sentMessage">
              Отправить
            </button>
            <button class="chat-modal-btn-cancel" @click="btn = !btn">
              Отмена
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
      messageBtn: '',
      url: '',
      btn: false
    }
  },
  props: [
    'sender'
  ],
  methods: {
    sentMessage() {
      let hour = new Date().getHours()
      let min = new Date().getMinutes()

      if (hour < 10) {
        hour = '0' + hour
      } else {
        hour == hour
      }

      if (min < 10) {
        min = '0' + min
      } else {
        min == min
      }
      const time = `${hour}:${min}`

      if (this.message.length) {
        const msg = {}
        msg.body = this.message.trim()
        msg.sendId = this.sender
        msg.time = time
        msg.imageUrl = this.url,
        this.$emit('message', msg)
      } else if (this.messageBtn.length) {
        const msg = {}
        msg.body = this.messageBtn.trim()
        msg.sendId = this.sender
        msg.time = time
        msg.imageUrl = this.url,
        this.$emit('message', msg)
      }
    }
  }
}
</script>

<style scoped>
.chat-button {
  display: flex;
  justify-content: space-between;
  background: #323232;
  width: 100%;
  padding: 15px 20px;
}
.chat-button input {
  width: 90%;
  font-family: 'RR';
  font-size: 14px;
  font-weight: 400;
  color: white;
}
.chat-button input::placeholder {
  color: #FFF;
}
.chat-button button {
  cursor: pointer;
}
.chat-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.35);
}
.chat-modal-wrap {
  width: 312px;
  border-radius: 28px;
  background: #f2f7ff;
  padding: 24px;
}
.chat-modal-title {
  color: #1c1b1f;
  font-family: "RR";
  font-size: 24px;
  font-weight: 400;
  margin-bottom: 16px;
}
.chat-modal-form {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.chat-modal-form-file, .chat-modal-form-text {
  padding: 20px;
  border-radius: 4px 4px 0px 0px;
  background: #e2edff;
  color: #49454f;
  font-family: "RR";
  font-size: 16px;
  font-weight: 400;
  border-bottom: 1px solid #000;
}
.chat-modal-btns {
  display: flex;
  flex-direction: row-reverse;
  gap: 10px;
}
.chat-modal-btn-send {
  padding: 10px 12px;
  border-radius: 20px;
  font-family: 'RM';
  font-size: 14px;
  font-weight: 500;
  color: #6750a4;
  text-transform: uppercase;
  transition: .3s linear;
  cursor: pointer;
}
.chat-modal-btn-send:hover {
  background: #e5ddfb;
}
.chat-modal-btn-cancel {
  padding: 10px 12px;
  border-radius: 20px;
  font-family: 'RM';
  font-size: 14px;
  font-weight: 500;
  color: #cf1b1b;
  text-transform: uppercase;
  transition: .3s linear;
  cursor: pointer;
}
.chat-modal-btn-cancel:hover {
  background: #dea7a7;
}
@media (max-width: 1024px) {
  .chat-button {
    padding: 15px 10px;
  }
}
@media (max-width: 800px) {
  .chat-button {
    padding: 8px 10px;
  }
}
@media (max-width: 800px) {
  .chat-button {
    padding: 8px 10px;
  }
}
</style>
