<template>
    <div class="user">
        <p>Name: {{ name }}</p>
        <p>Age: {{ age }} tuoi</p>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-6 col-6">
                <app-user-detail v-bind:age="age" v-on:ageWasUpdated="resetAge">
 
                    <template v-slot:default="slotProps">
                        {{ slotProps.user }}
                    </template>

                    <template v-slot:header>
                        <h1>title</h1>
                    </template>

                    <template v-slot:footer>
                        <h1>footer</h1>
                    </template>

                    <template v-slot:default>
                        <p>main content.</p>
                    </template>


                    <h1>Add slot</h1>
                </app-user-detail>
            </div>
            <div class="col-xs-12 col-sm-6 col-6">
                <app-user-edit v-bind:age="age" v-on:ageWasUpdated="resetAge"></app-user-edit>
            </div>

            <div class="col-xs-12 col-sm-6 col-6">
                <todo>
                    <template v-slot:todo="{ todo }">
                        <span v-if="todo.isComplete">✓</span>
                        {{ todo }}
                    </template>
                </todo>
            </div>

            <keep-alive>
                <component v-bind:is="appUserEdit"></component>
            </keep-alive>
        </div>
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';
    import Todo from './Todo.vue'

    export default {
        data: function () {
            return {
                name: 'linhdn',
                age: 16
            };
        },
        methods: {
            resetAge(age) {
                this.age = age
            }
        },
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit,
            todo: Todo,
        }
    }
</script>

<style scoped>
    .user{
        background: springgreen;
        text-align: center;
        padding: 20px;
    }
</style>
