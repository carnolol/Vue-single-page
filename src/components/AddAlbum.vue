<template>
  <div class="add-album">
    <h1>Add A New Album!</h1>
    <form @submit="addAlbum">
      <input type="text" placeholder="Album Name" name="name" v-model="name" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddAlbum",
  data() {
    return {
      artistName: "",
      artistPic: "",
      albumName: "",
      albumArtwork: "",
      songs: ""
    };
  },
  methods: {
    addAlbum(e) {
      e.preventDefault();
      console.log('HIT')
      const newAlbum = {
        id: Math.random(),
        name: this.name,
        pic: this.pic,
        albums: [
          {
            name: this.albumName,
            artwork: this.albumArtwork,
            songs: [this.songs],
          },
        ],
      }
      this.$emit('add-album', newAlbum)
    },
  },
};
</script>

<style lang="scss">
.add-album {
  margin: 40px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
