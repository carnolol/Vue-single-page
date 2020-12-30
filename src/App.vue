<template>
  <div id="app">
    <Header />
    <Hero />
    <AddAlbum v-on:add-album="addAlbum"/>
    <Artists v-bind:artists="artists"/>
    <footer class="footer">
      Just some filler text
    </footer>
  </div>
</template>

<script>
import Header from "./components/Header";
import Hero from "./components/Hero";
import Artists from "./components/Artists";
import AddAlbum from "./components/AddAlbum";

export default {
  name: "App",
  components: {
    Header,
    Hero,
    Artists,
    AddAlbum
  },
  data() {
    return {
      artists: [
        {
          id: 1,
          name: "AJR",
          pic: "https://s3-us-west-2.amazonaws.com/paradigm-media-library/music_artists/ajr-20190501.jpg",
          albums: [
            {
              id: 1,
              name: "Neotheater",
              artwork:
                "https://1.bp.blogspot.com/-OERxR6zLW7U/XWf2IKvsdfI/AAAAAAAAAAM/Y5_A1ht0Je0Ti-viNx5K4XDQ_rzoflMUwCLcBGAs/s1600/AJR.jpg",
              songs: [
                "Next Up Forever",
                "Birthday Party",
                "100 Bad Days",
                "Don't Throw Out my Legos",
                "Break My Face",
                "Turning Out Pt II",
                "The Entertainment's Here",
                "Karma",
                "Beats",
                "Wow, I'm Not Crazy",
                "Dear Winter",
                "Finale",
              ],
            },
            {
              id: 2,
              name: "The Click",
              artwork: "https://pbs.twimg.com/media/DHNSM4-WsAASGxY.jpg",
              songs: [
                "Overture",
                "The Good Part",
                "Weak",
                "Sober Up",
                "Drama",
                "Turning Out",
                "No Grass Today",
                "Three-Thirty",
                "Call My Dad",
                "I'm Not Famous",
                "Netflix Trip",
                "Bud Like You",
                "Come Hang Out",
              ],
            },
          ],
        },
        {
          id: 2,
          name: "NF",
          pic: "https://static.billboard.com/files/media/NF-rapper-press-photo-by-Jon_Taylor-Sweet-2017-billboard-1548-compressed.jpg",
          albums: [
            {
              id: 1,
              name: "The Search",
              artwork: "https://upload.wikimedia.org/wikipedia/en/1/1b/NF_-_The_Search.png",
              songs: [
                "The Search",
                "Leave Me Alone",
                "Change",
                "My Stress"
              ]
            }
          ]
        }
      ],
    };
  },
  methods: {
    addAlbum(newAlbum) {
      this.artists = [newAlbum, ...this.artists]
    },
  }
};
</script>

<style lang="scss">
@import './styles/App.scss';

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

img {
  height: auto;
  object-fit: scale-down;
  width: 100vw;
}
</style>
