<template>
  <div>
    <div class="chat-top">
      <img :src="images[img]" alt="">
      <div class="chat-top-info">
        <h2>{{ name }}</h2>
        <span>Онлайн</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'name',
    'img'
  ],
  data() {
    return {
      images: {
        alex: require('@/assets/img/alex.svg'),
        evgen: require('@/assets/img/evgen.svg')
      }
    }
  },
}
</script>

<style scoped>
.chat-top {
  display: flex;
  align-items: center;
  background: #323232;
  padding: 31px 20px;
  gap: 10px;
}
.chat-top-info {
  color: #FFF;
}
.chat-top-info h2 {
  font-family: 'RM';
  font-size: 18px;
  font-weight: 500;
}
.chat-top-info span {
  font-family: 'RL';
  font-size: 14px;
  font-weight: 300;
}
@media (max-width: 1024px) {
  .chat-top {
    padding: 15px 10px;
  }
}
@media (max-width: 800px) {
  .chat-top {
    padding: 8px 10px;
  }
}
@media (max-width: 500px) {
  .chat-top {
    padding: 8px 10px;
  }
}
</style>
