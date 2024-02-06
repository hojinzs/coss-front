<script>
  import Landing from '@/components/Landing.vue'
  import CommonHeader from '@/components/CommonHeader.vue'
  import ScrollContents from '@/components/ScrollContainer.vue'
  import TabMenu from "@/components/TabMenu.vue";

  export default {
    components: {
      CommonHeader,
      Landing,
      TabMenu,
      ScrollContents
    },
    mounted() {
      console.log("HOME");
    },
  }
</script>

<template>
  <main>
    <CommonHeader />
    <Landing />
    <ScrollContents />
    <TabMenu />
  </main>
</template>



