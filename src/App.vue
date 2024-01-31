<script setup>
import { onMounted, ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { gsap } from 'gsap'

const logoElement = ref(null)

onMounted(() => {
  gsap.to(logoElement.value, {
    scrollTrigger: logoElement.value,
    y: -50,
    yoyo: true,
    duration: 0.5, // 애니메이션 지속 시간
    repeat: -1, // 무한 반복
    ease: 'power1.inOut', // 이징 함수 설정
  });
})

</script>

<template>
  <header>
    <img ref="logoElement" id="logoElement" alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped lang="scss">
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;

  a {
    display: inline-block;
    padding: 0 1rem;
    border-left: 1px solid var(--color-border);

    &:first-of-type {
      border: 0;
    }

    .router-link-exact-active {
      color: var(--color-text);
    }

    .router-link-exact-active:hover {
      background-color: transparent;
    }

  }
}


@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
