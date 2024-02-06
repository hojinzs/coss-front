<script>
  import gsap from 'gsap'

  export default {
    mounted() {
      // 1) 로고 위치 초기 설정.
      const headerElement = this.$refs.header;
      gsap.set(headerElement, { });
      gsap.to(headerElement, { opacity: 1, duration: 1, delay: 3 });
    },
  }
</script>

<template>
  <Header ref="header">
    <div class="gnb">
      <a href="/" class="logo"><img src="/src/assets/logo.svg" alt=""></a>
      <nav>
        <a href="">메뉴1</a>
        <a href="">메뉴2</a>
        <a href="">메뉴3</a>
        <a href="">메뉴4</a>
      </nav>
    </div>
  </Header>
</template>


<style scoped>
Header {
  width: 100%;
  opacity: 0;
}
Header.fixed {
  position: fixed;
  top: 0;
}
Header .gnb {
  max-width: 1200px;
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  padding: 0 20px;
}

Header .logo img { width: 100px; }
nav {
  align-items: center;
  display: flex;
  flex-wrap: nowrap;
}
nav a {
  align-items: center;
  border: 0;
  border-radius: 6px;
  display: flex;
  font-size: 15px;
  font-weight: 500;
  height: 40px;
  justify-content: center;
  margin: 0 4px;
  opacity: .6;
  padding: 0 16px;
  transition: all .25s ease-in-out;
}
</style>