<script>
let id = 0;
export default{
  data(){
    return {
      todos: [
        {id: id++, text: "Clean room"}
      ],
      newTodo: ''
    };
  },
  methods: {
    addTodo(){
      if(this.newTodo === ''){
        return;
      }
      this.todos.push({id: id++, text: this.newTodo})
      this.newTodo = ''
    },
    removeTodo(todo){
      this.todos = this.todos.filter((t) => t !== todo);
    }
  }
}
</script>



<template>
  <h1>Todo App</h1>
  <ul>
    <form @submit.prevent="addTodo">
      <input placeholder="Type new todo item" v-model="newTodo">
      <button>Add</button>
    </form>
    <li v-for="t in todos" :key="t.id">
      {{ t.text }}
      <button v-on:click="removeTodo(t)">X</button>
    </li>
  </ul>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
li {
  list-style: none;
  padding: 5px;
}
li button {
  cursor: pointer;
  height: 30px;
  width: 30px;
  border-radius: 15px;
  color: #2c3e50;
  background-color: #fff;
  border: none;
  border: 1px solid rgba(22, 76, 167, 0.6)
}
input {
  padding:5px;
  text-align: center;
  height: 30px;
  width: 150px;
  border-radius: 15px;
  color: #2c3e50;
  background-color: #fff;
  border: none;
  border: 1px solid rgba(22, 76, 167, 0.6);
}
button {
  padding: 5px;
  text-align: center;
  height: 40px;
  width: 50px;
  border-radius: 15px;
  color: #2c3e50;
  background-color: #fff;
  border: none;
  border: 1px solid rgba(22, 76, 167, 0.6)
}
</style>
