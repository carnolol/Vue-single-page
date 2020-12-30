<template>
  <div>
    <div class="albums" v-for="(album, index) in albums" v-bind:key="index">
		<img @click="$emit('delete-album', album.id)"
		class=albums__delete 
		src="https://icons-for-free.com/iconfiles/png/512/delete+deny+no+out+sign+out+x+icon-1320196067039321214.png" 
		alt="delete artist"/>
		<img class="albums__artwork"
			:src="album.artwork"
			@click="console(album)"
			alt="album artwork"/>

		<p class="albums__name">name: {{ album.name }}</p>
		<p class="albums__songs" v-for="(song, index) in album.songs" :key="index">{{ song }}</p>

    </div>
  </div>
</template>

<script>
export default {
  name: "Albums",
  props: ["albums"],
  methods: {
    console(thing) {
      console.log("my thing:", thing);
    },
  },
};
</script>

<style lang="scss">
@import "../styles/Albums.scss";
</style>
