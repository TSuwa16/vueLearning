<template>
  <div>
      <v-toolbar dark color="indigo">
          <v-toolbar-tile class="white--text">My Todo</v-toolbar-tile>
      </v-toolbar>
      <v-list>
          <template v-for="(todo,i) in todos">
            <v-list-tile v-bind:key="i">
                <v-list-tile-content>
                    {{todo}}
                </v-list-tile-content>
                <v-list-tile-action>
                    <v-btn  v-on:click="deleteTodo(i)">
                        <v-icon style="font-size:18px">delete</v-icon>
                    </v-btn>
                </v-list-tile-action>
                <hr>
            </v-list-tile>
          </template>
      </v-list>

      <div class="bottom-right">
            <v-btn
                class="mx-2"
                fab
                dark
                large
                color="cyan"
                v-on:click="addTodo">
            <v-icon dark>
                mdi-pencil
            </v-icon>
          </v-btn>
      </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            todos:[]
        }
    },
    created(){
        this.todos = JSON.parse(localStorage.getItem('todos')) || [];
    },
    methods:{
        deleteTodo(i){
            this.todos.splice(i,1);
            localStorage.setItem('todos',JSON.stringify(this.todos));
        },
        addTodo(){
            this.$router.push('/todo/add');
        }
    }

}
</script>

<style>
 .bottom-right{
      position: fixed;
      bottom: 0 px; 
      right: 0 px;
      } 
</style>

