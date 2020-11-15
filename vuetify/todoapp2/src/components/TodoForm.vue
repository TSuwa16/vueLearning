<template>
  <div>
      <v-toolbar dark color="indigo">
          <router-link to ="/">
            <v-icon>←</v-icon>
          </router-link>
          <v-toolbar-title class="white--text" style="padding-left:20px">My Todo</v-toolbar-title>
      </v-toolbar>
      <v-text-field v-model="newTodo" placeholder="Input here..."></v-text-field>
      <v-btn fab dark color="indigo" v-on:click="addTodo()" class="white--text">
        <v-icon dark>
            mdi-plus
        </v-icon>
      </v-btn>
  </div>
</template>

<script>
export default {
    data(){
        return{
            newTodo:''
        }
    },
    methods:{
        addTodo(){
            if(this.newTodo === '')return;
            const todos = JSON.parse(localStorage.getItem('todos')) || [] ;
            todos.push(this.newTodo);
            localStorage.setItem('todos',JSON.stringify(todos));
            this.newTodo = '';
            this.$router.push('/');
        }
    }

}
</script>

<style>
    a{
        text-decoration: none;
    }
</style>