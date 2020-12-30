<template>
	<div class="add-album">
		<h1>Add A New Album!</h1>
		<form @submit="addAlbum" class="add-album__form">
			<input type="text" placeholder="Artist Name*" name="name" v-model="name" required="true" />
			<div class="add-album__artist-picture-wrapper">
				<img :src="this.handleArtistPicture()" class="artist-picture-wrapper__image"/>
				<input type="text" placeholder="Artist Picture" name="artistPic" v-model="artistPic" />
			</div>
			<input type="submit" />
		</form>
	</div>
</template>

<script>
export default {
	name: 'AddAlbum',
	data() {
		return {
			name: '',
			artistPic: '',
			albumName: '',
			albumArtwork: '',
			songs: ''
		};
	},
	methods: {
		addAlbum(e) {
			e.preventDefault();

			const newAlbum = {
				id: Math.floor(Math.random() * (1000 - 1) + 1),
				name: this.name,
				pic: this.artistPic,
				albums: [
					{
						name: this.albumName,
						artwork: this.albumArtwork,
						songs: [this.songs]
					}
				]
			};

			this.$emit('add-album', newAlbum);
			this.name = '';
			this.artistPic = '';
		},
		handleReset() {
			this.name = '';
		},
		handleArtistPicture() {
			if(this.artistPic) {
                return this.artistPic
            } else {
                return "https://www.atlantawatershed.org/wp-content/uploads/2017/06/default-placeholder.png"
            }
		}
	}
};
</script>

<style lang="scss">
@import '../styles/AddAlbum.scss';
</style>
