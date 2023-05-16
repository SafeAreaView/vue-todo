<script>
export default {
  name: "TodoList",
  data() {
    return {
      newTodo: "",
      idForToodo: 5,
      todos: [
        {
          id: 1,
          title: "First todo",
          Completed: false,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: this.idForToodo,
        title: this.newTodo,
        completed: false,
      });
      this.newTodo = "";
      this.idForToodo++;
    },
  },
};
</script>

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
        <button class="todo-add__btn">Add</button>
      </div>
    </div>
    <div class="todo-wrapper">
      <div v-for="todo in todos" :key="todo.id" class="todo-item">
        <input class="item-checkbox" type="checkbox" id="checkbox" />
        <span class="item-text">{{ todo.title }}</span>
        <button class="item-edit"></button>
        <button class="item-delete"></button>
      </div>
    </div>
  </div>
</template>

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
