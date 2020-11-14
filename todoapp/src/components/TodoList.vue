<template>
    <div>
        <h5>Todo List</h5>
        <ul>
            <li v-for="(todo,i) in todos" :key="i">
                {{todo}}
                <button @click="deleteTodo(i)">DEL</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props:['todos'],
    methods:{
        deleteTodo(i){
            this.$emit('delete',i);
        }
    }
    
}
</script>