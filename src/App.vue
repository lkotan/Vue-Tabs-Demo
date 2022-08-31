<script setup>
import { ref } from "vue";
import Tabs from "./components/Tabs.vue";
import Tab from "./components/Tab.vue";

const tabs = ref([
  "Showcased Accessories",
  "Interface Modules",
  "Network Access Points",
  "Network Routers",
]);
const version = APP_VERSION;
</script>

<template>
{{version}}
  <Tabs>
    <Tab v-for="tab in tabs" :key="tab" :title="tab">Hello {{ tab }}</Tab>
  </Tabs>
</template>
