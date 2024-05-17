<template>
  <div>
    <div class="chat-main">
        <div
          v-for="(message, index) in messages"
          :key="index"
          class="chat-main-item"
        >
          <div
            class="chat-main-item-content"
            :class="{
              send: message.sendId == sender,
              get: message.sendId != sender,
            }"
          >
            <span>{{ message.time }}</span>
            <div class="chat-main-item-content-text">
              <img
                v-if="message.imageUrl"
                :src="message.imageUrl"
                alt=""
                class="chat-main-item-content-img"
              >
              <p>{{ message.body }}</p>
            </div>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'messages',
    'sender',
    'messageBtn'
  ]
}
</script>

<style scoped>
.chat-main {
  height: 600px;
  overflow-y: auto;
}
.chat-main-item {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 10px;
}
.chat-main-item-content {
  align-items: center;
  display: flex;
}
.chat-main-item-content img {
  width: 100%;
  border-radius: 10px;
}
.chat-main-item-content.send {
  justify-content: flex-end;
  font-family: 'RR';
  font-size: 14px;
  font-weight: 400;
}
.chat-main-item-content.send .chat-main-item-content-text {
  border-radius: 15px 15px 0px 15px;
  background: #d0dcff;
  padding: 5px 10px;
  margin-left: 5px;
  font-family: 'RR';
  font-size: 16px;
  font-weight: 400;
}
.chat-main-item-content.get {
  flex-direction: row-reverse;
  justify-content: start;
  font-family: 'RR';
  font-size: 14px;
  font-weight: 400;
}
.chat-main-item-content.get .chat-main-item-content-text {
  border-radius: 15px 15px 15px 0px;
  background: #c4bfff;
  margin-right: 5px;
  padding: 5px 10px;
  font-family: 'RR';
  font-size: 16px;
  font-weight: 400;
  line-height: 20px;
}
.chat-main-item-content.get-text {
  min-width: 80%;
  word-wrap: break-word;
  word-break: break-all;
  display: flex;
  flex-direction: column;
  padding: 5px;
  text-align: center;
}
@media (max-width: 1400px) {
  .chat-main {
    height: 500px;
    overflow-y: auto;
  }
}
@media (max-width: 1024px) {
  .chat-main {
    height: 300px;
    overflow-y: auto;
  }
}
@media (max-width: 600px) {
  .chat-main {
    height: 200px;
    overflow-y: auto;
  }
}
@media (max-width: 500px) {
  .chat-main {
    height: 200px;
    overflow-y: auto;
  }
}
@media (max-width: 320px) {
  .chat-main {
    height: 100px;
    overflow-y: auto;
  }
}
</style>
