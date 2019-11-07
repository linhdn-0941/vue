<template>
    <div class="user-detail">
        <slot name="header"></slot>
        <h3>User Details</h3>
        <p>Age: {{ age }}</p>
        <button @click="editAge()">Change age</button>
        <slot></slot>
        <button type="submit">
            <slot>Submit</slot>
        </button>
        <slot v-bind:user="user">
            {{ user.lastName }}
        </slot>
        <slot name="footer"></slot>
    </div>
</template>

<script>
    import {eventBus} from '../main'
    export default {
        data: function () {
            return {
                user: {
                    firstName: 'Linh',
                    lastName: 'Duong'
                },
                user1: {
                    firstName: 'User1',
                    lastName: 'Of'
                }
            };
        },
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
