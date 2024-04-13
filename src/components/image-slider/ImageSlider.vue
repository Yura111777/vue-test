<script>
import { defineComponent } from "vue";
import Logo from "@/components/logo-screen/LogoScreen.vue";
import { gsap } from "gsap";

export default defineComponent({
  name: "ImageSlider",
  props: ["activeSlider"],
  components: { Logo },
  data() {
    return {
      images: [
        "src/assets/04header.jpg",
        "src/assets/03header.jpg",
        "src/assets/02header.jpg",
      ],
      activeSl: false,
    };
  },
  watch: {
    activeSlider(newValue, oldValue) {
      if (newValue) {
        const tl = gsap.timeline({ repeat: -1 });
        tl.to(this.$refs.images, {
          stagger: 0.5,
          keyframes: [{ visibility: "visible", duration: 0.5 }],
        });
      }
      return (this.activeSl = newValue);
    },
  },
});
</script>

<template>
  <div class="img-slider">
    <img
      src="../../assets/01header.jpg"
      v-if="!activeSl"
      class="first"
      alt=""
    />
    <span class="text">
      Digital Marketing
      <br />
      Agency
    </span>
    <img
      v-for="(image, index) in images"
      :key="index"
      :src="image"
      class="slider"
      ref="images"
      alt=""
    />
    <div class="img-slider-background"></div>
  </div>
</template>

<style scoped lang="scss">
.img-slider {
  min-height: 100vh;
  position: relative;
}
.text {
  position: absolute;
  top: 20px;
  right: 21px;
  z-index: 1;
  display: block;
  text-align: right;
  color: #e63e3a;
  text-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: 120%; /* 21.6px */
}
.slider {
  width: 100%;
  position: absolute;
  height: 100%;
  object-fit: cover;
  left: 0;
  top: 0;
  visibility: hidden;
}
.first {
  max-width: 100%;
  object-fit: cover;
  position: absolute;
  height: 100%;
}
.img-slider-background {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  background-color: rgba(0 0 0);
  z-index: 0;
}
</style>
