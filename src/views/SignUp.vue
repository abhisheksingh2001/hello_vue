<template>

    <div class="md-layout md-gutter">
        <div class="md-layout-item"></div>

        <div class="md-layout-item">
            <div>
                <form class="form" @submit.prevent="onSubmit">
                    <md-field>
                        <label>Name</label>
                        <md-input v-model.trim="name" @input="$v.name.$touch()"></md-input>

                        <div v-if="$v.name.$dirty">
                            <p class="error-message" v-if="!$v.name.required">
                                Name must not be empty.
                            </p>
                        </div>
                    </md-field>

                    <md-field>
                        <label>Mobile</label>
                        <md-input v-model.trim="mobile" @input="$v.mobile.$touch()"></md-input>

                        <div v-if="$v.mobile.$dirty">
                            <p class="error-message" v-if="!$v.mobile.required">
                                Mobile must not be empty.
                            </p>
                            <p class="error-message" v-if="!$v.mobile.minLength">
                                Mobile must be 10 characters long.
                            </p>
                        </div>
                    </md-field>

                    <md-field>
                        <label>Email</label>
                        <md-input v-model.trim="email" @input="$v.email.$touch()"></md-input>

                        <div v-if="$v.email.$dirty">
                            <p class="error-message" v-if="!$v.email.email">
                                Please enter a valid email address.
                            </p>
                            <p class="error-message" v-if="!$v.email.required">
                                Email must not be empty.
                            </p>
                        </div>
                    </md-field>

                    <md-field>
                        <label>Gender</label>
                        <md-select v-model.trim="gender">
                            <md-option value="fight-club">M</md-option>
                            <md-option value="godfather">F</md-option>

                            <div v-if="$v.gender.$dirty">
                                <p class="error-message" v-if="!$v.gender.required">
                                    Gender must not be empty.
                                </p>
                            </div>
                        </md-select>
                    </md-field>

                    <md-button class="md-dense md-raised md-primary" type="submit" :disabled="$v.$invalid">Register</md-button>
                </form>
            </div>
        </div>

        <div class="md-layout-item"></div>

    </div>

</template>

<script>
    import { validationMixin } from 'vuelidate'
    import {
        required,
        minLength,
        email
    } from 'vuelidate/lib/validators'

    export default {
        name: 'SignUp',
        mixins: [validationMixin],
        data () {
            return {
                name: '',
                mobile: '',
                email: '',
                gender: ''
            }
        },
        validations: {
            name: {
                required,
            },
            mobile: {
                required,
                minLength: minLength(10)
            },
            email: {
                required,
                email
            },
            gender: {
                required
            }
        },
        methods: {
            onSubmit () {
                // Make API call here to save user
            }
        }
    }

</script>

<style lang="scss" scoped>
    .md-progress-bar {
        position: absolute;
        top: 0;
        right: 0;
        left: 0;
    }
    .grid-container {
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: 100vh;
        align-items: center;
        justify-items: center;
    }
    .error-message {
        color: red;
    }
</style>
