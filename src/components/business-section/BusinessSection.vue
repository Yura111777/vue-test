<script>
import { defineComponent } from "vue";
import NavHeader from "@/components/business-section/components/NavHeader.vue";
import { gsap } from "gsap";

export default defineComponent({
  name: "BusinessSection",
  components: { NavHeader },
  props: ["startText"],
  data() {
    return {
      text: ["Growing", "businesses by", "building", "relationships"],
    };
  },
  mounted() {
    this.text = this.text.map((el) => {
      return { text: el.split("") };
    });
  },
  watch: {
    startText(newValue, oldValue) {
      if (newValue) {
        gsap.to(this.$refs.textHorizontalRef, {
          stagger: 0.05,
          keyframes: [{ visibility: "visible", duration: 0.05 }],
        });
      }
    },
  },
});
</script>

<template>
  <div class="business-section">
    <NavHeader></NavHeader>
    <h1>
      <span v-for="item in text" class="block">
        <span
          v-for="char in item.text"
          ref="textHorizontalRef"
          v-html="char === ' ' ? '&nbsp; ' : char"
        ></span>
      </span>
    </h1>
    <span class="caption">
      B2B Marketing & LinkedIn Lead <br />
      Generation agency
    </span>
  </div>
</template>

<style scoped lang="scss">
.business-section {
  padding: 18px 20px 0 19px;
  background-color: #e63e3a;
  min-height: 100vh;
  position: relative;
}
h1 {
  margin-top: 92px;
  text-align: right;
  color: #101820;
  font-size: 135px;
  font-style: normal;
  font-weight: 400;
  line-height: 96%; /* 129.6px */
  letter-spacing: -4.05px;
  @media (max-width: 1400px) {
    font-size: 110px;
  }
  .block {
    span {
      display: inline-flex;
      visibility: hidden;
    }
  }
}
.block {
  display: block;
}
.caption {
  color: #101820;
  left: 20px;
  bottom: 30px;
  position: absolute;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: 120.5%; /* 26.51px */
}
</style>
