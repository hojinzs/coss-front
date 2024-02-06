<template>
  <div class="landing" ref="landing">
    <div class="inner">
      <img src="/src/assets/logo.svg" alt="Logo" ref="logo" class="logo"/>
    </div>
  </div>
</template>

<script>
  import gsap from 'gsap';

  export default {
    mounted() {
      // 최초 / 스크롤 막기.
      const body = document.querySelector("body");
      body.classList.add("fixed");
      // 1) 로고 위치 초기 설정.
      const logoElement = this.$refs.logo;
      const dimmed = this.$refs.landing;
      gsap.set(logoElement, { transformOrigin: 'center center', duration: 1, delay: 1});
      gsap.to(logoElement, { opacity: .5, duration: 1, delay: 1 });
      gsap.to(logoElement, { opacity: 1, duration: 1, delay: 1 });
      gsap.to(logoElement, {transform: 'translate(0%, 0%)', width: 100 ,left: 20, top: 0, duration: 1, delay: 2, opacity: 1});
      // 1) 배경숨김
      gsap.set(dimmed, {})
      gsap.to(dimmed, { zIndex: -1, opacity: 0, duration: 1, delay: 2 } )
      setTimeout(() => {
        body.classList.remove("fixed");
      }, 3000);
    },
  };
</script>

<style scoped>
.landing {
  background-color: orange; /* 배경 색상 */
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  z-index: 1;
  position: fixed;
  left: 0;
  top: 0;
  transition: all, 1s;
}
.landing .logo {
  position: absolute;
  opacity: .4;
  z-index: 100;
  width: 200px;
  transform: translate(-50%, -50%);
}
</style>
