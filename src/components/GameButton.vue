<template>
    <button :class="'game-button click-cursor ' + this.class">
      <span class="title">{{ title }}</span>
    </button>
</template>

<script>
export default {
    props: [
      'title',
      'class'
    ],
}
</script>

<style scoped>
.game-button {
  position: absolute;
  background-image: url("../assets/images/game-btn.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  min-width: 31px;
  height: 10px;
  padding-left: 0;
  padding-right: 0;
  display: flex;
  transform: translateY(0);
  animation: buttonAnimation 2s infinite;
}

.title {
  font-size: 3.5px;
  font-weight: 600;
  font-family: Lora, serif;
  color: #000;
  padding: 0 3px;
  margin: auto;
  font-family: "Lora", Georgia, serif;

}

@keyframes buttonAnimation {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(3px);
  }
  100% {
    transform: translateY(0);
  }
}

</style>