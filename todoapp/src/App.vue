<template>
  <div>
    <todo-form v-on:add="addTodo($event)"></todo-form>
    <todo-list v-bind:todos="todos" v-on:delete="deleteTodo($event)"></todo-list>>
  </div>
</template>

<script>
import TodoForm from './components/TodoFrom.vue'
import TodoList from './components/TodoList.vue'

export default {
  data(){
    return{
      todos:[]
    }
  },
  created(){
    this.todos = JSON.parse(localStorage.getItem('todos')) || []; //ローカルストレージ
  },
  components:{
    'todo-form':TodoForm,
    'todo-list':TodoList
  },
  methods:{
    addTodo(newTodo){
      this.todos.push(newTodo);
      localStorage.setItem('todos',JSON.stringify(this.todos));
    },
    deleteTodo(i){
      this.todos.splice(i,1);
      localStorage.setItem('todos',JSON.stringify(this.todos));

    }
  }
}
</script>
