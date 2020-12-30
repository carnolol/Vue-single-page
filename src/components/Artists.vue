<template>
	<div>
		<div class="artists" v-for="artist in artists" v-bind:key="artist.id">
			<h1 class="artists__name">{{ artist.name }}</h1>
			<img class="artists__picture" :src="artist.pic" alt="Artists picture" />

			<!-- If Statement to detemine displaying the word Album if only 1 album fromt hat artist is added.  -->
			<p class="artists__text" v-if="artist.albums.length > 1">{{ artist.name }} has producded {{ artist.albums.length }} albums!</p>
			<p class="artists__text" v-else>{{ artist.name }} has producded only {{ artist.albums.length }} album :(</p>

			<Albums v-bind:albums="artist.albums" />
		</div>
	</div>
</template>

<script>
import Albums from './Albums';

export default {
	name: 'Artists',
	components: {
		Albums
	},
	props: ['artists']
};
</script>

<style lang="scss">
@import '../styles/Artists.scss';
</style>
