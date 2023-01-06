<template>
  <div id="app" class="flex container h-screen w-full">
    <right-side-bar @get-id="getId" @open-drop-down="openDropDown" :dropdown="dropdown" :id="id" :tabs="tabs" />

    <Tweet-list @add-new-tweet="addNewTweet" :tweets="tweets" :following="following" v-model:value="tweet.content" />

    <Trending-bar :trending="trending" :friends="friends" />
  </div>
</template>

<script>
import RightSideBar from '@/components/RightSideBar';
import TweetList from '@/components/TweetList';
import TrendingBar from '@/components/TrendingBar';
export default {
  name: 'app',
  components: {
    RightSideBar,
    TweetList,
    TrendingBar,
  },
  data() {
    return {
      tabs: [
        { icon: 'fas fa-home', title: 'Home', id: 'home' },
        { icon: 'fas fa-hashtag', title: 'Explore', id: 'explore' },
        { icon: 'far fa-bell', title: 'Notifications', id: 'notifications' },
        { icon: 'far fa-envelope', title: 'Messages', id: 'messages' },
        { icon: 'far fa-bookmark', title: 'Bookmarks', id: 'bookmarks' },
        { icon: 'fas fa-clipboard-list', title: 'Lists', id: 'lists' },
        { icon: 'far fa-user', title: 'Profile', id: 'profile' },
        { icon: 'fas fa-ellipsis-h', title: 'More', id: 'more' },
      ],
      id: 'home',
      dropdown: false,
      trending: [
        {
          top: 'Trending in TX',
          title: 'Gigi',
          bottom: 'Trending with: Rip Gigi',
        },
        { top: 'Music', title: 'We Won', bottom: '135K Tweets' },
        { top: 'Pop', title: 'Blue Ivy', bottom: '40k tweets' },
        { top: 'Trending in US', title: 'Denim Day', bottom: '40k tweets' },
        { top: 'Trending', title: 'When Beyonce', bottom: '25.4k tweets' },
      ],
      friends: [
        { src: 'elon.jpeg', name: 'Elon Musk', handle: '@teslaBoy' },
        { src: 'monk.jpeg', name: 'Adrian Monk', handle: '@detective:)' },
        { src: 'kevin.jpeg', name: 'Kevin Hart', handle: '@miniRock' },
      ],
      following: [
        {
          src: 'elon.jpeg',
          name: 'Elon Musk',
          handle: '@teslaBoy',
          time: '20 min',
          tweet: 'Should I just quarantine on mars??',
          comments: '1,000',
          retweets: '550',
          like: '1,000,003',
        },
        {
          src: 'kevin.jpeg',
          name: 'Kevin Hart',
          handle: '@miniRock',
          time: '55 min',
          tweet: 'Should me and the rock do another sub-par movie together????',
          comments: '2,030',
          retweets: '50',
          like: '20,003',
        },
        {
          src: 'elon.jpeg',
          name: 'Elon Musk',
          handle: '@teslaBoy',
          time: '1.4 hr',
          tweet: 'Haha just made a flame thrower. Shld I sell them?',
          comments: '100,000',
          retweets: '1,000,002',
          like: '5,000,003',
        },
        {
          src: 'elon.jpeg',
          name: 'Elon Musk',
          handle: '@teslaBoy',
          time: '1.4 hr',
          tweet: 'Just did something crazyyyyyyy',
          comments: '100,500',
          retweets: '1,000,032',
          like: '5,000,103',
        },
      ],
      tweets: [{ content: 'It is so nice outside!' }],
      tweet: { content: '' },
    };
  },
  watch: {
    tweet: {
      handler(val) {
        console.log(val);
      },
      deep: true,
    },
  },
  methods: {
    addNewTweet() {
      let newTweet = {
        content: this.tweet.content,
      };
      this.tweets.push(newTweet);
      this.tweet.content = '';
    },

    getId(id) {
      this.id = id;
    },
    openDropDown() {
      this.dropdown = !this.dropdown;
    },
  },
};
</script>
