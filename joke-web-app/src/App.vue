<template>
<section id='app'>
  <header class='header'>{{ title }}</header>
    <Button v-on:newJoke='getNewJoke()'/>
    <Joke 
    v-if='viewJoke'
    v-bind:currentJokeCategory='currentJoke.category' 
    v-bind:currentJoke='currentJoke.joke'
    />
  </section>
</template>

<script>
import Button from './components/Button';
import Joke from './components/Joke';
const axios = require('axios').default;

export default {
  name: 'App',
  components: {
    Button,
    Joke
  },

  data: function() {
    return {
      title: 'Jokes from the web!',
      viewJoke: false,
      currentJoke: {
      category: null,
      joke: null
    }
  }
},

  methods:{
    getJoke: async function(){
       const getJokeResponse = await axios.get('https://v2.jokeapi.dev/joke/Any?blacklistFlags=religious,racist,sexist,explicit&type=single');
       const getJoke = await getJokeResponse.data;
       this.currentJoke.category = getJoke.category;
       this.currentJoke.joke = getJoke.joke;
    },
    getNewJoke: function(){
      if(!this.viewJoke){
    this.viewJoke = true;
    } else {
      this.getJoke();
    }
  }
},

  created: function() {
    this.getJoke();
  }
};
</script>

<style>
.header {
  position: sticky;
  top:0;
  height: 130px;
  border-radius: 5px;
  background-color: #05668d;

}
body {
  background-color: #f0efeb
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.header {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 45px;
  font-family: "Fantasy";
  color: #f0f3bd;
}
</style>
