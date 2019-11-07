<template>
    <div class="user-edit">
        <h3>Edit User</h3>
        <p>Age: {{ age }}</p>
        <button @click="changeAge()">Change through parent</button>
        <button @click="changeAgeBus()">Change through event bus</button>
    </div>
</template>

<script>
    import {eventBus} from '../main'
    export default {
        props: ['age'],
        methods: {
            changeAge() {
                this.age = 21
                this.$emit('ageWasUpdated', this.age);
            },
            changeAgeBus() {
                this.age = 25
                eventBus.$emit('ageSentByBus', this.age);
            }
        }
    }
</script>

<style scoped>
    .user-edit{
        padding: 10px;
        background: gold;
    }
</style>
