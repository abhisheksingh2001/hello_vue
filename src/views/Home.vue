<template>
    <div class="home">
        <div style="flex: 1; text-align: right">
            <md-field md-inline style="background-color: burlywood;
                            width: 20%;
                            position: absolute;
                            right: 120px;
                            border-radius: 10px">
                <label>Search event name</label>
                <md-input v-model="text" v-on:keyup="handleInput"></md-input>
            </md-field>
        </div>
        <section class="hero is-dark">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">
                        Welcome to the Music Concert League
                    </h1>
                    <h2 class="subtitle">
                        Make sure you check out our upcoming events below
                    </h2>
                    <div class="button-block">
                        <button class="button is-xl is-dark">Sign Up to Browse Events</button>
                    </div>
                </div>
            </div>
        </section>
        <EventsList v-bind:filteredData="filteredEvent"/>
    </div>
</template>

<script>
    import EventsList from '../components/EvenList'
    export default {
        name: "home",
        components: {
            EventsList
        },
        data () {
            return {
                text: '',
                events: [
                    {
                        id: 1,
                        name: 'Charity Ball',
                        category: 'Fundraising',
                        description: 'Spend an elegant night of dinner and dancing with us as we raise money for our new rescue farm.',
                        featuredImage: 'https://placekitten.com/500/500',
                        images: [
                            'https://placekitten.com/500/500',
                            'https://placekitten.com/500/500',
                            'https://placekitten.com/500/500',
                        ],
                        location: '1234 Fancy Ave',
                        date: '12-25-2019',
                        time: '11:30'
                    },
                    {
                        id: 2,
                        name: 'Rescue Center Goods Drive',
                        category: 'Adoptions',
                        description: 'Come to our donation drive to help us replenish our stock of pet food, toys, bedding, etc. We will have live bands, games, food trucks, and much more.',
                        featuredImage: 'https://placekitten.com/500/500',
                        images: [
                            'https://placekitten.com/500/500'
                        ],
                        location: '1234 Dog Alley',
                        date: '11-21-2019',
                        time: '12:00'
                    }
                ],
                filteredEvent: [],
            }
        },
        methods: {
            handleInput: function () {
                this.filteredResources(this.text);
            },

            filteredResources (searchText){
                if(searchText){
                    console.log('hey',searchText);
                    let data =  this.events.filter((item)=>{
                        return item.name.startsWith(searchText);
                    });
                    console.log('heyy');
                    if (data.length > 0) {
                        this.filteredEvent = data;
                    }
                }else{
                    this.filteredEvent = this.events;
                }
            }
        },
        mounted() {
            // make API call here
            this.filteredEvent = this.events;
        }
    }

</script>

<style lang="scss" scoped>
    .hero {
        text-align: center;
        background-image: url('https://cdn.auth0.com/blog/vue-meetup/event-banner.png');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        height: 400px;
    }
    .hero-body .title {
        text-shadow: 4px 4px 4px rgba(0, 0, 0, 0.6);
        padding: 40px 0 20px 0;
        font-size: 60px;
    }
    .subtitle {
        text-shadow: 4px 4px 4px rgba(0, 0, 0, 0.7);
        font-size: 30px;
    }
    .button-block {
        text-align: center;
        margin-left: auto;
        margin-right: auto;
        width: 100%;
        position: absolute;
        bottom: -150px;
        .button {
            margin-right: 50px;
            padding-left: 50px;
            padding-right: 50px;
        }
        .welcome {
            width: 400px;
            padding: 10px;
            margin-left: auto;
            margin-right: auto;
        }
    }
    .is-xl {
        font-size: 1.7rem;
    }
</style>