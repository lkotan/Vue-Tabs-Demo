<script>
import { ref, provide } from "vue";

export default {
  setup(props, { slots }) {
    const tabTitles = ref(
      slots.default()[0].children.map((tab) => tab.props.title)
    );
    const selectedTitle = ref(tabTitles.value[0]);

    provide("selectedTitle", selectedTitle);
    return {
      tabTitles,
      selectedTitle,
    };
  },
};
</script>

<template>
  <div class="tabs">
    <ul class="tabs__header">
      <li
        v-for="title in tabTitles"
        :key="title"
        :class="{ selected: title === selectedTitle }"
        @click="selectedTitle = title"
      >
        {{ title }}
        <span class="material-icons"> keyboard_arrow_down </span>
      </li>
    </ul>
    <slot></slot>
  </div>
</template>

<style lang="css" scoped>
.tabs {
  width: auto;
  margin: 0 auto;
}
.tabs__header {
  margin-bottom: 10px;
  list-style: none;
  padding: 0;
  display: flex;
}
.tabs__header li {
  width: auto;
  display: flex;
  align-items: center;
  margin-right: 6px;
  padding: 10px 20px;
  border: 1px solid #9a9a9a;
  border-radius: 4px;
  cursor: pointer;
  transition: 0.1s all ease-out;
  background-color: #ffffff;
  color: #1a5888;
}
.tabs__header li span {
  color: gray;
  font-size: 32px;
}
.tabs__header li:hover {
  background-color: #d9e3ed;
}
.tabs__header li.selected {
  background-color: #1a5888;
  color: #ffffff;
}
.tabs__header li.selected span {
  color: #ffffff;
}
</style>
