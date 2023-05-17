<template>
  <div class="todo-wrapper">
    <h1 class="title">ToDo List</h1>
    <div class="add-task">
      <div class="todo-add">
        <input
          class="todo-add__input"
          placeholder="New Task"
          type="text"
          v-model="newTodo"
          @keyup.enter="addTodo"
        />
        <button class="todo-add__btn" @click="addTodo">Add</button>
      </div>
    </div>
    <div class="todo-items">
      <TodoItem
        v-for="(todo, index) in todos"
        :key="todo.id"
        :todo="todo"
        :index="index"
        @toggleCompleted="toggleCompleted(todo)"
        @toggleEdit="toggleEdit(todo)"
        @deleteTodo="deleteTodo(todo.id)"
        @saveTodo="saveTodo"
      />
    </div>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem.vue";

export default {
  name: "TodoList",
  components: {
    TodoItem,
  },
  data() {
    return {
      newTodo: "",
      idForTodo: 1,
      todos: [
        {
          id: 0,
          title: "First todo",
          completed: false,
          editing: false,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false,
        editing: false,
      });
      this.newTodo = "";
      this.idForTodo++;
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    toggleEdit(todo) {
      todo.editing = !todo.editing;
    },
    toggleCompleted(todo) {
      todo.completed = !todo.completed;
    },
    saveTodo() {
      this.todos.forEach((todo) => {
        todo.editing = false;
      });
    },
  },
};
</script>

<style scoped>
.todo-wrapper {
  width: 1200px;
  margin: 0 auto;

  display: flex;
  flex-direction: column;
  gap: 15px;
}
.todo-add {
  margin-bottom: 50px;
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

  transition: 0.3s;
}
.todo-add__btn:hover {
  background-color: rgb(49, 202, 202);
}
.todo-items {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
</style>
