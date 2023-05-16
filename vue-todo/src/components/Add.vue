<script>
export default {
  name: "Add",
  data() {
    return {
      newTodo: "",
      todos: [
        {
          id: 1,
          title: "First todo",
          Completed: false,
        },
      ],
    };
  },
};
</script>

<template>
  <div class="todo-add">
    <input
      class="todo-add__input"
      placeholder="New Task"
      type="text"
      v-model="newTodo"
    />
    <button class="todo-add__btn">Add</button>
  </div>
</template>
<style scoped>
.todo-add {
  margin-left: 5%;
  display: flex;
  justify-content: space-between;
}
.todo-add__input {
  width: 1000px;
  height: 50px;
  border: 1px solid black;
  border-radius: 10px;

  color: black;
  font-family: Roboto;
  font-size: 25px;
  padding-left: 40px;
}
.todo-add__btn {
  width: 50px;
  height: 50px;

  border: none;
  border-radius: 10px;

  font-family: Roboto;
  font-size: 20px;
  background-color: rgb(43, 122, 122);
  color: white;
}
</style>
