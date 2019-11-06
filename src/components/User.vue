<template>
    <div class="user">
        <p>Name: {{ name }}</p>
        <p>Age: {{ age }} tuoi</p>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-6 col-6">
                <app-user-detail v-bind:age="age" v-on:ageWasUpdated="resetAge"></app-user-detail>
            </div>
            <div class="col-xs-12 col-sm-6 col-6">
                <app-user-edit v-bind:age="age" v-on:ageWasUpdated="resetAge"></app-user-edit>
            </div>
        </div>
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

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
            appUserEdit: UserEdit
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
