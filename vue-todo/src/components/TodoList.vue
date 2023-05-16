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
    <div class="todo-wrapper">
      <div v-for="(todo, index) in todos" :key="todo.id" class="todo-item">
        <input
          class="item-checkbox"
          type="checkbox"
          :id="'checkbox-' + todo.id"
          :checked="todo.completed"
        />
        <span v-if="!todo.editing" class="item-text"
          >{{ index + 1 }}. {{ todo.title }}</span
        >
        <form v-else class="item-edit-form" @submit.prevent="saveTodo(todo)">
          <input class="item-edit-input" type="text" v-model="todo.title" />
          <button type="submit" class="item-edit-submit">Save</button>
        </form>
        <button class="item-edit" @click="toggleEdit(todo)"></button>
        <button class="item-delete" @click="deleteTodo(todo.id)"></button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
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
      this.idForTodo++; // Увеличиваем значение idForTodo
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    toggleEdit(todo) {
      todo.editing = !todo.editing;
    },
    saveTodo(todo) {
      todo.editing = false;
    },
    toggleCompleted(todo) {
      todo.completed = !todo.completed;
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
