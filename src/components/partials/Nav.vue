<template>
    <div>
        <md-toolbar class="md-accent" md-elevation="1" style="background-color: black">


            <md-button class="md-icon-button" @click="showNavigation = true">
            <md-icon>menu</md-icon>
            </md-button>

            <div>
                <h3 class="md-title" style="text-align: left; font-weight: 700">Music Concert League</h3>
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

        <Drawer v-bind:open='showNavigation'/>


        <!--<md-drawer :md-active.sync="showNavigation" md-swipeable style="background-color: blanchedalmond">-->
            <!--<span class="md-title" style="color: cornflowerblue;">My App name</span>-->
            <!--<md-list style="background-color: blanchedalmond">-->
                <!--<md-list-item>-->
                    <!--<md-icon>move_to_inbox</md-icon>-->
                    <!--<span class="md-list-item-text">Inbox</span>-->
                <!--</md-list-item>-->

                <!--<md-list-item>-->
                    <!--<md-icon>send</md-icon>-->
                    <!--<span class="md-list-item-text">Sent Mail</span>-->
                <!--</md-list-item>-->

                <!--<md-list-item>-->
                    <!--<md-icon>delete</md-icon>-->
                    <!--<span class="md-list-item-text">Trash</span>-->
                <!--</md-list-item>-->

                <!--<md-list-item>-->
                    <!--<md-icon>error</md-icon>-->
                    <!--<span class="md-list-item-text">Spam</span>-->
                <!--</md-list-item>-->
            <!--</md-list>-->
        <!--</md-drawer>-->

    </div>
</template>

<script>
    import Drawer from '../Drawer'
    export default {
        name: 'Nav',
        components: {
          Drawer
        },
        data () {
            return {
                text: '',
                showNavigation: false
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
    .md-drawer {
        width: 230px;
        max-width: calc(100vw - 125px);
    }
</style>