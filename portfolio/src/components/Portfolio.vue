<template>
  <div class="container">
    <h1>
      //My name is Tommy and I love
      <span class="typed-text">{{typeValue}}</span>
      <span class="cursor" :class="{'typing': typeStatus}"></span>
    </h1>
  </div>
</template>

<script>
export default {
  name: "Portfolio",
  data: () => {
    return {
      typeValue: "",
      typeStatus: false,
      typeArray: [
        "HTML",
        "CSS",
        "JavaScript",
        "React",
        "Vue",
        "NodeJs",
        "Postgresql"
      ],
      typingSpeed: 200,
      erasingSpeed: 100,
      nexTextDelay: 2000,
      typeArrayIndex: 0,
      charIndex: 0
    };
  },
  methods: {
    typeText() {
      if (this.charIndex < this.typeArray[this.typeArrayIndex].length) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue += this.typeArray[this.typeArrayIndex].charAt(
          this.charIndex
        );
        this.charIndex += 1;
        setTimeout(this.typeText, this.typingSpeed);
      } else {
        this.typeStatus = false;
        setTimeout(this.eraseText, this.newTextDelay);
      }
    },
    eraseText() {
      if (this.charIndex > 0) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue = this.typeArray[this.typeArrayIndex].substring(
          0,
          this.charIndex - 1
        );
        this.charIndex -= 1;
        setTimeout(this.eraseText, this.erasingSpeed);
      } else {
        this.typeStatus = false;
        this.typeArrayIndex += 1;
        if (this.typeArrayIndex >= this.typeArray.length)
          this.typeArrayIndex = 0;
        setTimeout(this.typeText, this.typingSpeed + 1000);
      }
    }
  },
  created() {
    setTimeout(this.typeText, this.newTextDelay + 200);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
h1 {
  font-size: 2.4rem;
  font-weight: normal;
  color: #fff;
  span.typed-text {
    color: #85cb33;
  }
  span.cursor {
    display: inline-block;
    margin-left: 2px;
    width: 4px;
    background-color: #fff;
  }
}
h1:after {
  content: "|";
  animation: cursorBlink 1s;
  animation-iteration-count: infinite;
  color: #fff;
}
span.cursor.typing {
  animation: none;
}
@keyframes cursorBlink {
  49% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
  99% {
    opacity: 0;
  }
}
</style>
