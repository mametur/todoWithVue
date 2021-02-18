<template>
    <div class="todo-item" v-bind:class="{'is-completed':todoList.completed}">
        <p>
            <input type="checkbox" v-bind:checked="todoList.completed" @change="markComplete">
            {{todoList.title}}
            <button class="del" @click="$emit('del-todo',todoList.id)">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props:["todoList"],
    data () {
        return {
            completeState: this.todoList
        }
    },
    methods:{
        markComplete(){
            console.log(this.completeState);
            this.completeState.completed = !( this.completeState.completed);
        }
    }

    }
</script>

<style scoped>
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
}
.is-completed {
    text-decoration: line-through;
}
.del {
    background: #ff0000;
    color: #fff;
    border:none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: ponter;
    float: right;
}

</style>