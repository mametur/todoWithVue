<template>
    <div>
        <form @submit.prevent="prepareNewTodo" >
            <input type="text" v-model="title" name="title"  placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>


<script>
export default {
    name:"AddTodo",
    data (){

        return {
            title:''
        }
    },
    methods: {
        prepareNewTodo(){
            const newTodo= {
                title: this.title,
                completed: false
            }
            // Send up to parent
            /*
             listens for the custom $emit event (childToParent) which is passed to your child component
            when fired it will grab the child's data and pass the value here (the parent component)
          */
            this.$emit('send-parent-todo', newTodo);
        }
    }
}
</script>

<style scoped>

form {
    display: flex;

}
input[type="text"] {
    flex:10;
    padding: 5px;
}
input[type="subpit"]{
    flex: 2;
}
</style>