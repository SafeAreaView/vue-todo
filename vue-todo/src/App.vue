<script setup>
import Item from "./components/Item.vue";
</script>

<template>
  <header class="header">
    <div class="header-wrapper">
      <h1 class="header-title">ToDo List</h1>
    </div>
  </header>
  <div class="wrapper">
    <h1 class="title">ToDo List</h1>
    <div class="add-task"></div>
    <div class="todo-wrapper">
      <Item />
      <Item />
      <Item />
    </div>
  </div>
</template>
<style src="./styles/main.css"></style>
