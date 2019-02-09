<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos1" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios";
export default {
  name: "Home",
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos1: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => {
          return (this.todos1 = this.todos1.filter(todo => todo.id !== id));
        })
        .catch(error => {
          return console.log(error);
        });
    },
    addTodo(todo) {
      const { title, completed } = todo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(res => {
          return (this.todos1 = [...this.todos, res.data]);
        })
        .catch(error => {
          return console.log(error);
        });
      this.todos1 = [...this.todos1, todo];
      // let newTodoList = this.todos1.unshift(todo);
      // console.log(newTodoList);
      // this.todos1 = newTodoList;
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => {
        return (this.todos1 = res.data);
      });
  }
};
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  margin: 5px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
