<template lang="html">

  <div class="body">

    <div v-bind:class="popularTweet">
      <img v-bind:src="tweet.img" alt="user profile">
      <p>{{tweet.name}} {{tweet.handle}}</p>
      <p>{{tweet.tweet}}</p>
      <p><img src="https://cdn4.iconfinder.com/data/icons/free-ui/64/v-10-512.png" alt="" class="heart"> {{tweet.likes}}</p>
    </div>

  </div>

</template>

<script>
export default {
  name: 'tweet-item',
  props: ['tweet'],
  computed: {
    popularTweet: function() {
      if (this.tweet.likes >= 10) {
        return "popularTweet"
      } else return "tweet"
    }
  }
}
</script>

<style lang="css" scoped>

  /* .body {
    display: flex;
    align-items: center;
    justify-content: space-between;
  } */

  .tweet {
    border-radius: 2px;
    background-color: #e0f2e9;
    border: 1px solid black;
    opacity: 50%;
    margin: 10px 0;
    padding: 0px 5px;
    padding-top: 5px;
  }

  .popularTweet {
    border-radius: 2px;
    background-color: #e0f2e9;
    border: 1px solid black;
    /* box-shadow: 5px 5px 1px red; */
    margin: 10px 0;
    padding: 0px 5px;
    padding-top: 5px;
  }

  .heart {
    width: 11px;
    background-size: 100%;
  }

  img {
    width: 50px;
  }
</style>
