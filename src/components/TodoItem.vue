<template>
  <div class="todo-item bg-black" @click="$emit('toggleCompleted')">
    <input
      class="item-checkbox"
      type="checkbox"
      :id="'checkbox-' + todo.id"
      :checked="todo.completed"
    />
    <span v-if="!todo.editing" class="item-text">
      {{ index + 1 }}. {{ todo.title }}
    </span>
    <form v-else class="item-edit-form" @submit.prevent="$emit('saveTodo')">
      <input class="item-edit-input" type="text" v-model="todo.title" />
      <button type="submit" class="item-edit-submit">Save</button>
    </form>
    <button class="item-edit" @click="$emit('toggleEdit')"></button>
    <button class="item-delete" @click="$emit('deleteTodo')"></button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object,
    index: Number,
  },
};
</script>

<style>
.todo-item {
  width: inherit;
  height: 100px;

  padding: 0px 20px;

  display: flex;
  gap: 32px;
  align-items: center;

  border: 1px solid black;
}
.bg-black {
  background-color: rgb(74, 80, 85);
}
.item-delete {
  width: 32px;
  height: 32px;
  border: none;

  background: url("/public/images/delete-icon.png") 0 0 / cover no-repeat;
}

.item-edit {
  width: 32px;
  height: 32px;
  border: none;

  background: url("/public/images/edit-icon.png") 0 0 / cover no-repeat;
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
  width: 900px;
  font-family: Roboto;
  font-size: 30px;
}
</style>
