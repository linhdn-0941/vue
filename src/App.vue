<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12">
                <!-- <app-user></app-user> -->
                <todo-list v-bind:todos="todos">

                </todo-list>
                <createTodo v-on:create-todo="createTodo"></createTodo>>
            </div>
        </div>
    </div>
</template>

<script>
    import User from './components/User.vue';
    import TodoList from './components/TodoApp/TodoList.vue'
    import CreateTodo from './components/TodoApp/CreateTodo.vue'

    export default {
        components: {
            appUser: User,
            todoList: TodoList,
            createTodo: CreateTodo,
        },
        data() {
            return {
                todos: [
                    {
                        title: 'Todo A',
                        project: 'Project A',
                        done: false,
                    },
                    {
                        title: 'Todo B',
                        project: 'Project B',
                        done: true,
                    },
                    {
                        title: 'Todo C',
                        project: 'Project C',
                        done: false,
                    },
                    {
                        title: 'Todo D',
                        project: 'Project D',
                        done: false,
                    }
                ],
            };
        },
        methods: {
            createTodo(todo) {
                this.todos.push(todo);
                swal("Success!", "Created!", "success");
            }
        }
    }
</script>
