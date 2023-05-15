import '@/styles/item.css';
<script>
export default {
  name: "Item",
};
</script>

<template>
  <div class="todo-item">
    <label class="item-label" for="checkbox">
      <input class="item-checkbox" type="checkbox" id="checkbox" />
      <span class="item-text">todotodotodo</span>
    </label>
    <img src="../assets/edit-icon.png" alt="" class="item-edit" />
    <img src="../assets/delete-icon.png" alt="" class="item-delete" />
  </div>
</template>
<style src="../styles/item.css"></style>

<!-- <label class="item-label" for="checkboxInput">
      <input class="item-checkbox" type="checkbox" id="checkboxInput" />
      <span class="item-text">todotodotodo</span>
    </label> -->
