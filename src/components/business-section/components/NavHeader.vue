<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "NavHeader",
});
</script>

<template>
  <nav class="nav">
    <div class="left-side">
      <a href="/" class="logo">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="79"
          height="51"
          viewBox="0 0 79 51"
          fill="none"
        >
          <path
            d="M21.609 36.3C21.661 37.28 21.661 38.157 21.661 39.137V45.74H37.389V51H0L0 39.138C0 30.061 1.806 23.563 10.778 23.563C16.709 23.563 19.545 26.399 20.778 30.99L37.384 22.326V28.206L21.609 36.3ZM4.435 45.74H17.225V38.726C17.225 33.208 16.657 28.979 10.882 28.979C5.107 28.979 4.435 33.208 4.435 38.726L4.435 45.74Z"
            fill="#101820"
          />
          <path
            d="M63.822 3.8147e-06C70.579 3.8147e-06 76.508 3.042 78.004 10.211H72.898C71.66 5.931 67.329 4.43501 63.615 4.43501C60.728 4.43501 55.672 5.72501 55.672 9.902C55.672 13.202 58.251 14.853 61.759 15.626L66.09 16.606C71.814 17.843 78.672 20.009 78.672 27.538C78.672 34.81 71.866 38.729 64.441 38.729C55.623 38.729 50.052 33.881 49.072 26.456H54.229C55.209 31.612 58.772 34.294 64.543 34.294C70.112 34.294 73.26 31.715 73.26 28.002C73.26 24.031 69.855 22.484 65.213 21.402L60.572 20.422C55.417 19.287 50.31 16.399 50.31 10.211C50.31 3.042 57.788 3.8147e-06 63.822 3.8147e-06Z"
            fill="#101820"
          />
          <path d="M44.398 51V45.069H50.328V51H44.398Z" fill="#101820" />
        </svg>
      </a>
      <ul>
        <li><a href="">Services</a></li>
        <li><a href="">Case Studies</a></li>
        <li><a href="">Blog</a></li>
      </ul>
    </div>
    <div class="right-side">
      <ul>
        <li><a href="">We're hiring</a></li>
        <li><a href="">Contacts</a></li>
      </ul>
      <button class="next-button">
        <span class="icon-next-arrow"></span> Book a call
      </button>
    </div>
  </nav>
</template>

<style scoped lang="scss">
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.left-side {
  display: flex;
  align-items: center;
  .logo {
    margin-right: 174px;
    @media (max-width: 1400px) {
      margin-right: 36px;
    }
  }
}
.right-side {
  display: flex;
  align-items: center;
  .next-button {
    margin-left: 118px;
    @media (max-width: 1400px) {
      margin-left: 36px;
    }
  }
}
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  li {
    margin-left: 78px;
    display: inline-flex;
    @media (max-width: 1400px) {
      margin-left: 36px;
    }
    a {
      color: #101820;
      font-size: 22px;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
      text-decoration: none;
      @media (max-width: 1400px) {
        font-size: 18px;
      }
    }
  }
}
.next-button {
  border: 0;
  outline: none;
  padding: 0 18px;
  background: #101820;
  color: #e63e3a;
  font-size: 22px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  height: 51px;
  width: 330px;
  box-sizing: border-box;
  @media (max-width: 1400px) {
    font-size: 18px;
  }
}
.icon-next-arrow {
  color: #e63e3a;
  font-size: 20px;
  margin-right: 65px;
  @media (max-width: 1400px) {
    font-size: 18px;
    margin-right: 30px;
  }
}
</style>
