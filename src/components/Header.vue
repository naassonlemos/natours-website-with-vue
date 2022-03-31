<template>
  <header class="header">
    <div class="logo-box">
      <img src="../assets/logo-white.png" alt="logo" class="logo" />
    </div>

    <div class="text-box">
      <h1 class="heading-primary">
        <span class="heading-primary-main">Outdoors</span>
        <span class="heading-primary-sub">is where life happens</span>
      </h1>

      <Button
        text="Discover our tours"
        type="white"
        hrefLink="https://www.google.com/"
      />
    </div>
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  components: { Button },
  name: "HeaderComponent",
};
</script>

<style lang="scss" scoped>
.header {
  height: 95vh;
  background-image: linear-gradient(
      to right,
      rgba(126, 213, 111, 0.8),
      rgba(40, 180, 133, 0.8)
    ),
    url(../assets/hero.jpg);
  background-size: cover;
  background-position: top;
  position: relative;

  clip-path: polygon(0 0, 100% 0, 100% 75vh, 0 100%);
}

.logo-box {
  position: absolute;
  top: 40px;
  left: 40px;
}

.logo {
  height: 35px;
}

.text-box {
  position: absolute;
  top: 40%;
  left: 50%; // the content start from the middle
  transform: translate(-50%, -50%); // move the content to the middle
  text-align: center;
}

.heading-primary {
  color: #fff;
  text-transform: uppercase;

  backface-visibility: hidden;
  margin-bottom: 60px;
}

.heading-primary-main {
  display: block;
  font-size: 60px;
  font-weight: 400;
  letter-spacing: 35px;

  animation-name: moveInLeft;
  animation-duration: 1s;
  animation-timing-function: ease-out;

  // animation-fill-mode: both;
}

.heading-primary-sub {
  display: block;
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 17.4px;
  animation: moveInRight 1s ease-out;
}

@keyframes moveInLeft {
  0% {
    opacity: 0;
    transform: translateX(-100px);
  }
  80% {
    opacity: 1;
    transform: translateX(10px);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes moveInRight {
  0% {
    opacity: 0;
    transform: translateX(100px);
  }
  80% {
    opacity: 1;
    transform: translateX(10px);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>
