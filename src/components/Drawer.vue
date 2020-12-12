<template>
    <div>
        <!--<md-button class="md-icon-button" @click="showNavigation = true">-->
            <!--<md-icon>menu</md-icon>-->
        <!--</md-button>-->

        <md-drawer :md-active.sync="a" md-swipeable style="background-color: blanchedalmond">
            <span class="md-title" style="color: cornflowerblue;">My App name</span>
            <md-list style="background-color: blanchedalmond">
                <md-list-item>
                    <md-icon>move_to_inbox</md-icon>
                    <span class="md-list-item-text">Inbox</span>
                </md-list-item>

                <md-list-item>
                    <md-icon>send</md-icon>
                    <span class="md-list-item-text">Sent Mail</span>
                </md-list-item>

                <md-list-item>
                    <md-icon>delete</md-icon>
                    <span class="md-list-item-text">Trash</span>
                </md-list-item>

                <md-list-item>
                    <md-icon>error</md-icon>
                    <span class="md-list-item-text">Spam</span>
                </md-list-item>
            </md-list>
        </md-drawer>
    </div>
</template>

<script>
    export default {
        name: "Drawer",
        props: ['open'],
        data() {
            return {
                a: this.$props.open
            }
        },
        watch: {
            open: function (newVal, oldVal) { // watch it
                console.log(oldVal);
                this.a = newVal;
            }
        },
    }
</script>

<style lang="scss" scoped>
    .md-drawer {
        width: 230px;
        max-width: calc(100vw - 125px);
    }
</style>