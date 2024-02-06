<template>
  <div>
    <div class="tab-area">
      <div class="tab-content">
        <div v-for="(tab, index) in tabs" :key="index" v-show="activeTab === index">
          {{ tab.content }}
        </div>
      </div>
      <div class="tab-buttons">
        <button v-for="(tab, index) in tabs" :key="index" @click="changeTab(index)" :class="{ active: activeTab === index }">
          {{ tab.title }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    const tabs = ref([
      { title: 'Tab 1', content: 'Content for Tab 01' },
      { title: 'Tab 2', content: 'Content for Tab 02' },
      { title: 'Tab 3', content: 'Content for Tab 03' },
    ]);
    const activeTab = ref(0);
    const changeTab = (index) => {
      activeTab.value = index;
    };
    return {
      tabs,
      activeTab,
      changeTab,
    };
  },
};
</script>

<style>
.tab-area {
  display: flex;
  position: absolute;
  z-index: 10;
}
.tab-buttons {
  display: flex;
  flex-direction: column;
}
.tab-buttons button {
  padding: 10px;
  margin: 5px;
  cursor: pointer;
  border: 1px solid #ddd;
  background-color: #f9f9f9;
}
.tab-buttons button.active {
  background-color: #ddd;
}
.tab-content div {
  padding: 20px;
  border: 1px solid #ddd;
}
.tab-content div.show {
  display: block;
}
</style>