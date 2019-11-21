<template>
<div class="main" :class="darkClass">
  <div class="container" @click="setWhite">
    <img class="white-img" src="./assets/img/white_bkg.png" />
    <img class="white-img ship" src="./assets/img/white_ship.png" />
    <img class="dark-img" src="./assets/img/dark_bkg.png" />
    <img class="dark-img ship" src="./assets/img/dark_ship.png" />
  </div>
</div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      isWhite: false
    };
  },
  computed: {
    darkClass() {
      return this.isWhite ? "" : "dark"
    }
  },
  methods: {
    setWhite() {
      this.isWhite = true;
    }
  }
};
</script>

<style lang="stylus">
html, body {
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.main {
  display: flex;
  align-items: center;
  background #e6dbce;

  &.dark {
    background: #050505;

    .container {
      border-color #ddd;
    }
    .dark-img {
      opacity 1
    }
    .white-img {
      opacity: 0
    }
  }
}

.container {
  width: 600px;
  height: 350px;
  overflow: hidden;
  margin: auto;
  position: relative;
  cursor pointer
  border 3px solid black
}

.main, img, .container {
  transition: all 4s;
}

.main, img {
  position: absolute;
  width: 100%;
  left: 0;
  top: 0;
  bottom: 0;
  right: 0;
}

.dark-img {
  opacity 0
}

.ship {
  animation: shipAnim 4s alternate infinite;
}

@keyframes shipAnim {
  0% {
    transform: rotateZ(0.7deg);
  }

  40% {
    transform: translateY(3px) rotateZ(0);
  }

  100% {
    transform: rotateZ(-0.7deg);
  }
}

@media screen and (max-width: 610px) {
  .container {
    width 350px
    height: 205px
  }
}
</style>
