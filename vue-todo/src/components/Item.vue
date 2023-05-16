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
<style scoped>
.todo-item {
  width: inherit;
  height: 100px;

  padding: 0px 20px;

  display: flex;
  gap: 32px;
  align-items: center;

  border: 1px solid black;
}

.item-delete {
  width: 32px;
  height: 32px;
}

.item-edit {
  width: 32px;
  height: 32px;
}

.item-checkbox {
  width: 32px;
  height: 32px;
}

.item-label {
  width: 1000px;

  display: flex;
  gap: 30px;
}

.item-text {
  font-family: Roboto;
  font-size: 30px;
}
</style>

<!-- <label class="item-label" for="checkboxInput">
      <input class="item-checkbox" type="checkbox" id="checkboxInput" />
      <span class="item-text">todotodotodo</span>
    </label> -->
