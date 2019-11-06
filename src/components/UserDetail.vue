<template>
    <div class="user-detail">
        <h3>User Details</h3>
        <p>Age: {{ age }}</p>
        <button @click="editAge()">Change age</button>
    </div>
</template>

<script>
    import {eventBus} from '../main'
    export default {
        props: ['age'],
        methods: {
            editAge() {
                this.age += 1
                this.$emit('ageWasUpdated', this.age)
            }
        },
        created() {
            eventBus.$on('ageSentByBus', (age) => {
                this.age = age
            })
        }
    }
</script>

<style scoped>
    .user-detail{
        padding: 10px;
        background: red;
    }
</style>
