<template>
  <div class="app">
    <h1 class="title">Todo List</h1>
    <ul class="todo-list">
      <li v-for="todo in todos" :key="todo.id">
        <span class="todo-title">{{ todo.title }}</span>
        <button class="edit-btn" @click="editTodo(todo)">Edit</button>
        <button class="delete-btn" @click="deleteTodo(todo)">Delete</button>
      </li>
    </ul>
    <form @submit.prevent="addTodo">
      <input v-model="newTodoTitle" type="text" class="input-field" placeholder="Enter new todo">
      <button class="add-btn" type="submit">Add Todo</button>
    </form>
    <form v-if="editingTodo" @submit.prevent="updateTodo">
      <input v-model="editingTodo.title" type="text" class="input-field" placeholder="Edit todo">
      <button class="update-btn" type="submit">Update Todo</button>
      <button class="cancel-btn" @click="cancelEdit">Cancel</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [
        { title: 'Belajar Vue', id: 1 },
        { title: 'Belajar React', id: 2 }
      ],
      newTodoTitle: '',
      editingTodo: null
    }
  },
  methods: {
    addTodo() {
      this.todos.push({ title: this.newTodoTitle, id: Date.now() })
      this.newTodoTitle = ''
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter(t => t.id !== todo.id)
    },
    editTodo(todo) {
      this.editingTodo = todo
    },
    updateTodo() {
      this.editingTodo = null
    },
    cancelEdit() {
      this.editingTodo = null
    }
  }
}
</script>

<style>
.app {
  max-width: 400px;
  margin: 40px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
  color: #4CAF50;
}

.todo-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.todo-list li {
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

.todo-list li:last-child {
  border-bottom: none;
}

.todo-title {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 10px;
}

.edit-btn {
  background-color: #4CAF50;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.edit-btn:hover {
  background-color: #3e8e41;
}

.delete-btn {
  background-color: #4CAF50;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.delete-btn:hover {
  background-color: #3e8e41;
}

.input-field {
  width: 100%;
  height: 40px;
  margin-bottom: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.add-btn {
  background-color: #4CAF50;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.add-btn:hover {
  background-color: #3e8e41;
}

.update-btn {
  background-color: #4CAF50;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.update-btn:hover {
  background-color: #3e8e41;
}

.cancel-btn {
  background-color: #4CAF50;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.cancel-btn:hover {
  background-color: #3e8e41;
}
</style>