<template>
    <div>
        <input type="text" placeholder="first name" v-model="firstName" />
        <input type="text" placeholder="last name" v-model="lastName" />
        <button @click="save">Submit</button>
    </div>
</template>

<style scoped>
    button {
        color: red;
    }
</style>

<script>
    export default {
        data() {
            return {
                firstName: '',
                lastName: ''
            }
        },
        methods: {
            save() {
                const { firstName, lastName } = this;
                this.$emit('saved', { firstName, lastName });
            }
        }
    };
</script>

