<script>
import { defineComponent } from "vue";
import { gsap } from "gsap";

export default defineComponent({
  name: "Logo",
  props: ["startLogo"],

  data() {
    return {
      logoTextHorizontal: "Respect",
      logoTextVertical: ".Studio",
      ctx: null,
    };
  },
  mounted() {
    this.logoTextHorizontal = this.logoTextHorizontal.split("");
    this.logoTextVertical = this.logoTextVertical.split("");
  },
  watch: {
    startLogo(newValue, oldValue) {
      if (newValue) {
        this.ctx = gsap.context((self) => {
          gsap.to(this.$refs.logoTextHorizontalRef, {
            duration: 1,
            stagger: 0.1,
            visibility: "visible",
            onComplete: () => {
              gsap.to(this.$refs.logoScreen, {
                duration: 0.5,
                y: "-100%",
                onComplete: () => {
                  this.$emit("slider", true);
                },
              });
            },
          });
          gsap.to(this.$refs.logoTextVerticalRef, {
            duration: 1,
            stagger: 0.1,
            visibility: "visible",
          });
        }, this.$refs.logoFolder);
      }
    },
  },
  unmounted() {
    this.ctx.revert();
  },
});
</script>

<template>
  <div ref="logoFolder">
    <div class="logo">
      <div class="logo-horizontal">
        <span v-for="item in logoTextHorizontal" ref="logoTextHorizontalRef">{{
          item
        }}</span>
      </div>
      <div class="logo-vertical">
        <span v-for="item in logoTextVertical" ref="logoTextVerticalRef">{{
          item
        }}</span>
      </div>
    </div>
    <div class="logo-screen" ref="logoScreen"></div>
  </div>
</template>

<style scoped lang="scss">
.logo {
  position: absolute;
  z-index: 3;
  top: 0;
  left: 0;
}
.logo-horizontal {
  padding-left: 20px;
  span {
    display: inline-flex;
    visibility: hidden;
    font-size: 66px;
    color: #e63e3a;
    text-align: right;
    -webkit-text-stroke-width: 1;
    -webkit-text-stroke-color: #000;
    line-height: normal;
  }
}
.logo-vertical {
  transform: rotate(90deg) translate(87px, 81px);
  display: flex;
  align-items: flex-end;
  span {
    display: inline-flex;
    visibility: hidden;
    font-size: 66px;
    color: #e63e3a;
    text-align: right;
    -webkit-text-stroke-width: 1;
    -webkit-text-stroke-color: #000;
    line-height: normal;
    & ~ span {
      padding-bottom: 11px;
    }
  }
}
.logo-screen {
  z-index: 2;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: #101820;
}
</style>
