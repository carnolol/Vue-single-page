<template>
	<div class="add-album">
		<h1>Add A New Album!</h1>
		<form @submit="addAlbum" class="add-album__form">
            <p>Add some info about the Artist!</p>
			<input type="text" placeholder="Artist Name*" name="name" v-model="name" required="true" />

			<div class="add-album__artist-picture-wrapper">
				<img :src="this.handleArtistPicture()" class="artist-picture-wrapper__image" />
				<input type="text" placeholder="Artist Picture" name="artistPic" v-model="artistPic" />
			</div>

            <p>Add some info about their Ablums!</p>

			<input type="text" placeholder="Album Name*" required="true" name="albumName" v-model="albumName" />

			<div class="add-album__artist-picture-wrapper">
				<img class="artist-picture-wrapper__image" :src="this.handleAlbumArtwork()" />
				<input type="text" placeholder="Album Artwork*" required="false" name="albumArtwork" v-model="albumArtwork" />
			</div>

			<input type="text" placeholder="Seperate multiple songs with a comma!" required="false" name="songs" v-model="songs" />

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
						songs: this.songs.split(',')
					}
				]
			};

			this.$emit('add-album', newAlbum);
			this.name = '';
			this.artistPic = '';
			this.albumName = '';
			this.albumArtwork = '';
			this.songs = '';
        },
		handleArtistPicture() {
			if (this.artistPic) {
				return this.artistPic;
			} else {
				return 'https://www.atlantawatershed.org/wp-content/uploads/2017/06/default-placeholder.png';
			}
		},
		handleAlbumArtwork() {
			if (this.albumArtwork) {
				return this.albumArtwork;
			} else {
				return 'https://www.atlantawatershed.org/wp-content/uploads/2017/06/default-placeholder.png';
			}
		}
	}
};
</script>

<style lang="scss">
@import '../styles/AddAlbum.scss';
</style>
