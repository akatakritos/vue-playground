<template>
    <div>
        <div>
        <input type="text" placeholder="first name" v-model="firstName" @keyup="validate"/>
        <input type="text" placeholder="last name" v-model="lastName"  @keyup="validate"/>
        </div>
        <div v-if="message" class="error">{{ message }}</div>
        <button @click="save" :disabled="!canClick">Submit</button>
    </div>
</template>

<style scoped>
</style>

<script>
    export default {
        data() {
            return {
                firstName: '',
                lastName: '',
                submitted: false,
                valid: false,
                message: null,
            }
        },
        methods: {
            save() {
                this.submitted = true;

                var valid = this.validate();
                if (!valid)
                    return;

                const { firstName, lastName } = this;
                this.$emit('saved', { firstName, lastName });
            },

            validate() {
                const { firstName, lastName } = this;

                if (firstName == "") {
                    this.valid = false;
                    this.message = "first name required";
                    return false;
                }

                if (lastName == "") {
                    this.valid = false;
                    this.message = "last name required";
                    return false;
                }

                this.message = null;
                this.valid = true;
                return true;
            }
        },
        computed: {
            canClick() {
                return !this.submitted || this.valid;
            }
        }

    };
</script>

<style>
    .error {
        color: red;
    }
</style>

