<template lang="html">

  <div id="container">
    <div class="title">
      <h1>Dweeter</h1> <img class="titleimg" src="https://image.flaticon.com/icons/svg/40/40486.svg" alt="icon">
    </div>

    <h4 class="totalLikes">Total Likes: {{totalLikes}}</h4>

    <form v-on:submit.prevent="saveTweet">
      <p>New Dweet</p>
      <input class="nameHandle" placeholder="Name" type="text" v-model="newTweet.name" required/>
      <input class="nameHandle" placeholder="Handle" type="text" v-model="newTweet.handle" required/>
      <br>
      <input placeholder="Your Tweet" class="yourTweet" type="text" v-model="newTweet.tweet" required/>
      <br>
      <input type="submit" value="Post Tweet" />
    </form>
    <br>

    <div id="filterInput" class="filterLikes">
      <h3>Filter Dweets by Likes</h3>
      <input class="nameHandle" placeholder="0" type="number" v-model.number="filterAmount" />
    </div>
    <br>

    <tweet-item v-for="(tweet, index) in filteredTweets" :key="index" :tweet="tweet"></tweet-item>
  </div>

</template>

<script>

import Tweet from './components/Tweet.vue'

export default {
  name: 'app',
  data() {
  return {
    tweets:[
      {
        id: 1,
        name: 'James',
        handle: '@jokerjames',
        img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
        tweet: "If you don't succeed, dust yourself off and try again.",
        likes: 10,
      },
      {
        id: 2,
        name: 'Fatima',
        handle: '@fantasticfatima',
        img: 'https://semantic-ui.com/images/avatar2/large/molly.png',
        tweet: 'Better late than never but never late is better.',
        likes: 12,
      },
      {
        id: 3,
        name: 'Xin',
        handle: '@xeroxin',
        img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
        tweet: 'Beauty in the struggle, ugliness in the success.',
        likes: 18,
      }
    ],
    newTweet: {
      name: "",
      handle: "",
      img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
      tweet: "",
      likes: Math.floor(Math.random() * 15)
    },
    filterAmount: 0,
    // popularTweet: 0
  }
},
components: {
  'tweet-item': Tweet
},
computed: {
  totalLikes: function() {
    return this.tweets.reduce((runningTotal, tweet) => {
      return runningTotal + tweet.likes;
    }, 0);
  },
  filteredTweets: function() {
    return this.tweets.filter((tweet) => {
      return tweet.likes >= this.filterAmount;
    })
  }
},
methods: {
  saveTweet: function() {
    this.tweets.unshift(this.newTweet);

    this.newTweet = {
      name: "",
      handle: "",
      img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
      tweet: "",
      likes: Math.floor(Math.random() * 15)

    };
  }
}
}
</script>

<style lang="css" scoped>
  #container {
    height: 100%;
    width: 50%;
    margin: 0 auto;
    background-color: #5b7b7a;
    padding: 30px;
    font-family: 'Manrope', sans-serif;
  }

  .title {
    display: flex;
    align-items: center;
  }

  .titleimg {
    background-size: 100%;
    width: 30px;
  }

  .tweet {
    border-radius: 2px;
    background-color: #e0f2e9;
    border: 1px solid black;
    margin: 10px 0;
    padding: 0px 5px;
    padding-top: 5px;
    display: flex;
    align-items: flex-end;
    flex-direction: row;
  }

  .nameHandle {
    border: 01px solid black;
    margin-bottom: 1px;
  }

  .yourTweet {
    border: 01px solid black;
    /* display: flex; */
    /* justify-content: center; */
    width: 99.3%;
    height: 30px;
  }

  .totalLikes {
    border-radius: 2px;
    width: 110px;
    background-color: #CEB5A7;
    border: 1px solid black;
    margin: 10px 0;
    padding: 0px 5px;
    /* padding-top: 5px; */
    text-align: center;
  }

  .filterLikes {
    border-radius: 2px;
    width: 200px;
    background-color: #e0f2e9;
    border: 1px solid black;
    margin: 10px 0;
    padding: 0px 5px;
    padding-bottom: 5px;
    /* text-align: center; */
  }

  form {
    border-radius: 2px;
    display: flex;
    align-items: baseline;
    flex-direction: column;
    background-color: #e0f2e9;
    border: 1px solid black;
    margin: 10px 0;
    padding: 0px 5px;
    padding-bottom: 5px;
  }

  input[type=submit] {
    border: 1px solid black;
  }
</style>
