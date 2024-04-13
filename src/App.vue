<script setup>
import StartScreen from "@/components/StartScreen.vue";
import ImageSlider from "@/components/image-slider/ImageSlider.vue";
import { onMounted, ref } from "vue";
import Logo from "@/components/logo-screen/LogoScreen.vue";
import BusinessSection from "@/components/business-section/BusinessSection.vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import ConsistentSection from "@/components/consistent-section/ConsistentSection.vue";

const startLogo = ref(false);
const activeSlider = ref(false);
const startText = ref(false);
function setStartLogo() {
  startLogo.value = true;
}

function setActiveSlider(status) {
  activeSlider.value = status;
}

onMounted(() => {
  gsap.registerPlugin(ScrollTrigger);
  gsap.defaults({ ease: "none", duration: 2 });
  const tl = gsap.timeline();
  tl.to(".img-slider-background", {
    opacity: 0.7,
    onComplete: () => {
      startText.value = true;
    },
  });
  ScrollTrigger.create({
    animation: tl,
    trigger: ".img-sl",
    start: "top top",
    end: "+=100%",
    scrub: true,
    pin: true,
    pinSpacing: false,
  });
  tl.from(".caption", {
    opacity: 1,
    duration: 0.5,
    onComplete: () => {
      gsap.to(".words", {
        stagger: 0.05,
        keyframes: [{ visibility: "visible", duration: 0.05 }],
        onStart: () => {
          gsap.from(".color-block", {
            duration: 1,
            stagger: 0.05,
            height: "0px",
          });
          gsap.to(".before", {
            duration: 2,
            opacity: 1,
          });
        },
      });
    },
  });
  ScrollTrigger.create({
    animation: tl,
    trigger: ".consistent-section",
    start: "top top",
    end: "+=4000px",
    scrub: 1,
    pin: false,
    pinSpacing: false,
  });
});
</script>

<template>
  <div>
    <StartScreen @startLogo="setStartLogo"></StartScreen>
    <div class="img-sl">
      <Logo :startLogo="startLogo" @slider="setActiveSlider"></Logo>
      <ImageSlider :activeSlider="activeSlider"></ImageSlider>
    </div>
    <BusinessSection
      :startText="startText"
      class="business-section"
    ></BusinessSection>
    <ConsistentSection class="consistent-section"></ConsistentSection>
  </div>
</template>

<style scoped>
.business-section {
  position: relative;
  z-index: 1;
}
</style>
