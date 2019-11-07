<template>
    <ul>
        <li
            v-for="todo in todos"
            v-bind:key="todo.id"
            >
            <slot name="todo" v-bind:todo="todo">
                {{ todo }}
            </slot>
        </li>
    </ul>
</template>

<script>
    export default {
        data: function () {
            return {
                todos: [
                    {
                        'id': 1,
                        'name': 'ABC',
                        'isComplete': true
                    },
                    {
                        'id': 2,
                        'name': 'XYZ',
                        'isComplete': false
                    },
                    {
                        'id': 3,
                        'name': 'KICM',
                        'isComplete': true
                    }
                ],
                todo: 'todo',
            };
        },
        computed: {
            filteredTodos() {
                return this.todos.filter((todo) => {
                    return todo.isComplete
                })
            }
        }
    }
</script>

<style>

</style>