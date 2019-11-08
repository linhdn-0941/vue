<template>
    <div>
        <div class='ui centered card'>
            <todo
            v-for="(todo, index) in todos"
            v-bind:todo="todo"
            v-bind:key="index"
            v-on:delete-todo="deleteTodo"
            v-on:complete-todo="completeTodo"
            >
            </todo>
        </div>
    </div>
</template>

<script>
import Todo from './Todo.vue';

export default {
    props: ['todos'],
    components: {
        todo: Todo,
    },
    methods: {
        deleteTodo(todo) {
            const todoIndex = this.todos.indexOf(todo);
            this.todos.splice(todoIndex, 1);
        },
        completeTodo(todo) {
            const todoIndex = this.todos.indexOf(todo);
            this.todos[todoIndex].done = true;
            swal("Success!", "Completed!", "success");
        }
    }
}
</script>

<style>

</style>
