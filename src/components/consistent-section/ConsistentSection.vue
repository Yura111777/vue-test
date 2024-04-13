<script>
import { defineComponent } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default defineComponent({
  name: "ConsistentSection",
  data() {
    return {
      text: ["Consistent leads flow to streamline", "Your business growth."],
      blocks: [
        171, 266, 341, 305, 194, 266, 341, 423, 305, 407, 509, 597, 445, 682,
      ],
      before: [27, 53, 61, 58, 30, 63, 55, 63, 71, 76, 67, 88, 78, 90],
    };
  },
  mounted() {
    this.text = this.text.map((el) => {
      return { text: el.split("") };
    });
  },
  computed: {
    blockWidth() {
      return `calc(100% / ${this.blocks.length})`;
    },
  },
});
</script>

<template>
  <div class="consistent-section">
    <div>
      <h2>
        <span v-for="item in text" class="block">
          <span
            v-for="char in item.text"
            ref="textHorizontalRef"
            class="words"
            v-html="char === ' ' ? '&nbsp; ' : char"
          ></span>
        </span>
      </h2>
      <p ref="caption" class="caption">
        We combine disruptive marketing techniques with proven tech solutions to
        provide maximum business value.
      </p>
    </div>
    <div>
      <div
        v-for="(item, index) in blocks"
        class="color-block"
        :style="{ height: `${item}px`, width: blockWidth }"
      >
        <div class="before">{{ before[index] }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.consistent-section {
  background-color: #fff;
  padding: 0 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
h2 {
  color: var(--dark-text, #101820);
  padding-top: 107px;
  font-size: 82px;
  font-style: normal;
  font-weight: 400;
  line-height: 96%; /* 78.72px */
  margin-bottom: 58px;
  @media (max-width: 1400px) {
    font-size: 60px;
  }
}
p {
  opacity: 0;
  color: #101820;
  margin-top: 0;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: 120.5%; /* 26.51px */
  max-width: 578px;
  @media (max-width: 1400px) {
    font-size: 18px;
  }
}
.block {
  display: block;
  span {
    visibility: hidden;
  }
}
.color-block {
  background-color: #e63e3a;
  border: 0.5px solid #fff;
  box-sizing: border-box;
  display: inline-flex;
  margin-bottom: 1px;
  position: relative;
  .before {
    position: absolute;
    color: #e63e3a;
    bottom: 100%;
    width: 100%;
    text-align: center;
    opacity: 0;
  }
}
</style>
