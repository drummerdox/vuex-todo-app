<template>
    <div id="app">
        <PostForm></PostForm>
        <h1>{{postsCount}}</h1>
        <div class="post" v-for="post in allPosts" :key="post.id">
            <h2>{{post.title}}</h2>
            <p>{{post.body}}</p>
        </div>
    </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld.vue'
    import PostForm from "./components/PostForm";
    import {mapGetters, mapActions} from 'vuex'

    export default {
        name: 'App',
        components: {
            HelloWorld,
            PostForm
        },
        // computed: {
        //     allPosts() {
        //         return this.$store.getters.allPosts();
        //     }
        // },
        methods: mapActions(['fetchPosts']),
        computed: mapGetters(['allPosts', 'postsCount']),
        async mounted() {
            // const res = await fetch('https://jsonplaceholder.typicode.com/posts');
            // this.posts = await res.json();

            //deprecated becouse of mapActions
            //await this.$store.dispatch("fetchPosts");

            await this.fetchPosts(4);
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
