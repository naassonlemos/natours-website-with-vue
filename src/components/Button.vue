<template>
  <div>
    <a :href="hrefLink" target="_blank" :class="buttonStyles">
      {{ text }}
    </a>
    <!-- <pre>
      {{ hrefLink }} - {{ type }} - {{ text }}
    </pre> -->
  </div>
</template>

<script>
export default {
  name: "ButtonComponent",
  props: {
    text: {
      type: String,
      required: true,
      default: "Put some text here",
    },
    type: {
      type: String,
      required: true,
      //   default: "white",
      validator(value) {
        return ["white", "green"].includes(value);
      },
    },
    hrefLink: {
      type: String,
      required: false,
      default: "#",
    },
  },
  computed: {
    buttonStyles() {
      if (this.type === "white") {
        return "btn btn-white btn-animated";
      } else if (this.type === "green") {
        return "btn btn-green";
      } else return this.type;
    },
  },
};
</script>

<style scoped>
.btn:link,
.btn:visited {
  text-transform: uppercase;
  text-decoration: none;
  padding: 15px 40px;
  display: inline-block;
  border-radius: 100px;
  transition: all 0.2s;
  position: relative;
}

.btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.btn:active {
  transform: translateY(-1px);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}

.btn-white {
  background-color: #fff;
  color: #777;
}

.btn::after {
  content: "";
  display: inline-block;
  height: 100%;
  width: 100%;
  border-radius: 100px;
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  transition: all 0.4s;
}

.btn-white::after {
  background-color: #fff;
}

.btn:hover::after {
  transform: scaleX(1.4) scaleY(1.6);
  opacity: 0;
}

@keyframes moveInBottom {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

.btn-animated {
  animation: moveInBottom 0.5s ease-out 0.75s;
  animation-fill-mode: backwards;
}
</style>
