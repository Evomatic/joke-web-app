<template>
    <article class='joke-article'>
        <h1 class='category'>category: {{ currentJokeCategory }}</h1>
        <p class='joke'>{{ currentJoke }}</p>
    </article>
</template>
<script>
export default {
   name: 'Joke',
   props: [ 'currentJoke', 'currentJokeCategory' ] 
};
</script>
<style>
    .category{
        font-family: "Fantasy";
        font-size: 35px;
        color: #05668d;
    }
    .joke {
        font-family: "Fantasy";
        font-size: 30px;
        color:#00a896
    }





</style>