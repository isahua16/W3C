<template>
    <div class="song_app"> 
        <section class="song_player">
            <div v-if="selected_song === ``" >
                <h3>Please select a song</h3>
            </div>
            <div v-else class="song_playing_card">
                <img class="player_img" :src="this.selected_song[`image_url`]" alt="Song Image">
                <p>{{this.selected_song[`title`]}}</p>
                <p>{{this.selected_song[`artist`]}}</p>
            </div>
        </section>  
        <section class="song_library">
            <article :title="song[`title`]" :artist="song[`artist`]" :image="song[`image_url`]" :song_id="song[`song_id`]" @click="select_song" class="song_card" v-for="song in songs" :key="song[`song_id`]">
                <img class="library_img" :src="song[`image_url`]" alt="Song Image">
                <p>{{song[`title`]}}</p>
                <p>{{song[`artist`]}}</p>
            </article>
        </section>
    </div>
</template>

<script>
    export default {
        methods: {
            select_song: function(event)
            {
                let clicked_song = {
                    title: event[`target`].getAttribute(`title`),
                    artist: event[`target`].getAttribute(`artist`),
                    song_id: event[`target`].getAttribute(`song_id`),
                    image_url: event[`target`].getAttribute(`image`)
                }
                this.selected_song = clicked_song;
            }
        },
        data() {
            return {
                selected_song: ``,
                songs: [
                    {
                        title: `Teenage Drug`,
                        artist: `Ethan Gruska`,
                        song_id: 1,
                        image_url: `https://images.unsplash.com/photo-1509114397022-ed747cca3f65?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1635&q=80`
                    },
                    {
                        title: `Nicole`,
                        artist: `Taylor Ashton`,
                        song_id: 2,
                        image_url: `https://images.unsplash.com/photo-1500099817043-86d46000d58f?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1587&q=80`
                    },
                    {
                        title: `Causeway Road`,
                        artist: `Adam Baldwin`,
                        song_id: 3,
                        image_url: `https://images.unsplash.com/photo-1487260211189-670c54da558d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1587&q=80`
                    }   
                ]
            } 
        },
    }
</script>

<style scoped>
    .song_app {
        width:100%;
        min-height: 100vh;
        display:grid;
        place-items: center;
    }
    
    .song_player {
        width:100%;
        display:grid;
        place-items: center;
    }
    .song_playing_card {
        width:50%;
        padding:25px;
        display:grid;
        place-items: center;
        box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
    }

    .player_img {
        height: 250px;
        width: 250px;
        object-fit: cover;
    }
    .library_img {
        height: 100px;
        width: 100px;
        object-fit: cover;
    }

    .song_library {
        display:grid;
        width:50%;
        row-gap: 12px;
    }

    .song_card {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        place-items: center;
        padding:10px;
        box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
    }
</style>