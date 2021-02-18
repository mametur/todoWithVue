<template>
    <div>
        <div v-for="(todo,index) in myTodos" v-bind:key="index">
           <TodoItem  v-bind:todoList="todo" v-on:del-todo="$emit('del-todo',todo.id)" />
        </div>
    </div>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
    name:"Todos", // component name
    props: ["myTodos"],
    components: {
        TodoItem
    }
}
</script>

<style scoped>

</style>