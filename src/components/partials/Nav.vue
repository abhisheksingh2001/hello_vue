<template>
    <div>
        <md-toolbar class="md-accent" md-elevation="1" style="background-color: black">
            <div>
                <h3 class="md-title" style="text-align: left; font-weight: 700">Animal Rescue League</h3>
            </div>

            <div style="padding: 10px;">
                <router-link to="/" style="padding: 10px;">
                    <span>Home</span>
                </router-link>
                <router-link to="/about" style="padding: 10px">
                    <span>About</span>
                </router-link>
            </div>

            <div style="flex: 1; text-align: right">
                    <md-button class="md-raised" style="background-color: dodgerblue">Sign In</md-button>
            </div>

        </md-toolbar>
    </div>
</template>

<script>
    export default {
        name: 'Nav',
        data () {
            return {
                text: ''
            }
        },
        methods: {
            handleInput: function () {
                return this.text
            }
        }
    }
</script>

<style lang="scss" scoped>
    .md-toolbar + .md-toolbar {
        margin-top: 16px;
    }
</style>