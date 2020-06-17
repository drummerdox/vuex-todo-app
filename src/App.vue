<template>
    <div id="app">
        <div class="post" v-for="post in allPosts" :key="post.id">
            <h2>{{post.title}}</h2>
            <p>{{post.body}}</p>
        </div>
    </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld.vue'
    import {mapGetters} from 'vuex'

    export default {
        name: 'App',
        components: {
            HelloWorld
        },
        // computed: {
        //     allPosts() {
        //         return this.$store.getters.allPosts();
        //     }
        // },
        computed: mapGetters(['allPosts']),
        async mounted() {
            // const res = await fetch('https://jsonplaceholder.typicode.com/posts');
            // this.posts = await res.json();

              await this.$store.dispatch("fetchPosts");
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
        width: 400px;
    }

    .post {
        border: 1px solid gray;
        border-radius: 5px;
        margin-bottom: 1rem;
    }
</style>
