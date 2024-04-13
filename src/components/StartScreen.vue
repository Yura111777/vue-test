<script>
import { defineComponent } from "vue";
import { gsap } from "gsap";

export default defineComponent({
  name: "StartScreen",
  data() {
    return {
      count: [
        "02",
        "06",
        "12",
        "24",
        "48",
        "56",
        "64",
        "76",
        "82",
        "98",
        "100",
      ],
      ctx: null,
    };
  },

  mounted() {
    this.ctx = gsap.context((self) => {
      const numbers = self.selector(".start-screen-count");
      document.querySelector("body").classList.add("active");
      numbers.forEach((el) => {
        gsap.to(this.$refs.numbers, {
          stagger: 0.25,
          keyframes: [
            { visibility: "visible", duration: 0.25 },
            { visibility: "hidden", duration: 0.25 },
          ],
          onComplete: () => {
            document.querySelector("body").classList.remove("active");
            this.$refs.startScreen.style.display = "none";
            this.$emit("startLogo", true);
          },
        });
      });
    }, this.$refs.startScreen);
  },
  unmounted() {
    this.ctx.revert();
  },
});
</script>

<template>
  <div ref="startScreen" class="start-screen">
    <span class="start-screen-count" ref="numbers" v-for="item in count">
      {{ item }}
    </span>
  </div>
</template>

<style lang="scss">
body {
  overflow-x: hidden;
  &.active {
    overflow: hidden;
  }
}
.start-screen {
  position: fixed;
  width: 100%;
  height: 100%;
  display: block;
  background: transparent;
  top: 0;
  left: 0;
  z-index: 3;
  &-count {
    position: absolute;
    bottom: 0;
    right: 0;
    color: #e63e3a;
    text-align: right;
    text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    -webkit-text-stroke-width: 1;
    -webkit-text-stroke-color: #000;
    font-size: 230px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    visibility: hidden;
  }
}
</style>
