<template>
  <div>
    <div class="text-center mt-[20vh]">
      <h1 >Hello, Rowena!</h1>
      <h1>T O D O</h1>
      <input placeholder="Create new to-do" type="text" v-model="todo" class="text-center w-2/5 mt-[3vh] border border-gray-300 text-gray-900 text-m rounded-md focus:ring-blue-50s focus:border-blue-500 p-2.5 dark:border-gray-600 dark:placeholder-gray-400 dark:text-gray-600 dark:focus:ring-blue-500 dark:focus:border-blue-500"/>
    </div>
    <div class="items-center text-center mt-1">
      <button v-on:click="handleSubmit" class="text-center border px-2 rounded-lg border-black hover:bg-blue-300 hover:border-blue-300 text-sm">Submit</button>
    </div>
    <TodoList :todos="todos" :select-todo="selectTodo" />
  </div>
</template>

<script>
import TodoList from '~/components/TodoList.vue';

export default {
  data: function() {
    return {
      todo: "",
      todoId: "",
      todos: [],
    };
  },

  components: { TodoList },
  mounted: function(){
    this.getTodo();
  },

  methods: {
    addTodo: function () {
      fetch('http://localhost:8080/todo', {
        headers: {
          'Content-Type': 'application/json',
        },
        method: "POST",
        body: JSON.stringify({
          title: this.todo
        }),
      })
      alert("Added successfully.")
      this.getTodo()
      this.todo = ""
    },

    getTodo: async function(){
      const postTodo = await fetch('http://localhost:8080/todo')
      const todoList = await postTodo.json()
      this.todos = todoList
    },

    selectTodo: async function(todo){
      this.todoId = todo.id;
      this.todo = todo.title;
    },

    editTodo: async function(){
      const putTodo = await fetch('http://localhost:8080/todo', {
        headers: {
        'Content-Type': 'application/json',
        },
        method: "PUT",
        body: JSON.stringify({
          id: this.todoId,
          title: this.todo
        }),
      })
      alert("Edited successfully.")
      const saveTodo = await putTodo.json();
      this.getTodo();
      this.todo = ""
    },

    handleSubmit: function(){
      if (!this.todoId){
        this.addTodo();
      } else{
        this.editTodo();
      }
    }
  },
}
</script>
