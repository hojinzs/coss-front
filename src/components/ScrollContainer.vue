<template>
  <div class="scroll-wrap">
    <div class="first">first</div>
    <div id="container" class="scrollContainer" ref="container">
      <section class="module pink">Slide 1</section>
      <section class="module yellow">Slide 2</section>
      <section class="module purple">Slide 3</section>
      <section class="module orange">Slide 4</section>
    </div>
    <div class="last">last</div>
  </div>
</template>

<script>
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import { onMounted } from 'vue';
gsap.registerPlugin(ScrollTrigger);
export default {
  setup() {
    onMounted(() => {
      let sections = gsap.utils.toArray("section");
      gsap.to(sections, {
        xPercent: -100 * (sections.length - 1),
        ease: "none",
        scrollTrigger: {
          trigger: document.querySelector("#container"),
          pin: true,
          scrub: 1,
          snap: 1 / (sections.length - 1),
          end: () => "+=" + document.querySelector("#container").offsetWidth
        }
      });

    })
  }
};
</script>

<style scoped>
html {
  overflow-y: scroll;
  height: 100%;
  -webkit-overflow-scrolling: touch;
  overflow-scrolling: touch;
}
body {
  overflow-y: visible;
  position: relative;
  height: unset;
}
html, body {
  overflow-x: hidden;
  margin: 0;
}
.scroll-wrap .last,
.scroll-wrap .first {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: skyblue;
}
.scroll-wrap .last {
  background: #ddd;
}

.scrollContainer {
  width: 400%;
  height: 100vh;
  display: flex;
  flex-wrap: nowrap;
}
.module {
  height: 100vh;
  width: 100vw;
  display: inline-flex;
}
.pink {
  background-color: pink;
}
.yellow {
  background-color: yellow;
}
.purple {
  background-color: purple;
}
.orange {
  background-color: orange;
}

.other {
  display: block;
  background: skyblue;
  border: 1px solid pink;
}
</style>
