<template>
  <div id="app">
    <transition-group>
      <img
        v-for="i in imgs"
        width="25%"
        src="./assets/logo.png"
        :key="i.id"
        class="card"
      />
    </transition-group>
    <button @click="stap">STAP</button> <button @click="stat">STAT</button>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld
  },

  data() {
    return {
      imgs: [
        { src: "./assets/logo.png", id: "1" },
        { src: "./assets/logo.png", id: "2" },
        { src: "./assets/logo.png", id: "3" },
        { src: "./assets/logo.png", id: "4" }
      ]
    };
  },

  methods: {
    stap() {
      clearInterval();
    },
    stat() {
      setInterval(() => {
        let first = this.imgs.shift();
        this.imgs.push(first);
      }, 500);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.card {
  transition: all 0.5s;
}
.card-enter,
.card-leave-to {
  opacity: 0;
  transform: scale(0);
}
.card-enter-to {
  opacity: 1;
  transform: scale(1);
}

.card-leave-active {
}

.card-move {
  opacity: 1;
  transition: all 0.5s;
}
</style>
