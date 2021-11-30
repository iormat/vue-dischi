<template>
	<div id="app">
		<Loader/>

        <AppHeader @getResults="filteredDiscsArr" :genres="genresArr"/>

		<AppMain :selectedGenre="genreToSearch" @genreOptions="getGenresArr"/>

		<AppFooter/>
	</div>
</template>

<script>
import Loader from './components/Loader.vue';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';

export default {
	name: 'App',
	components: {
		Loader,
		AppHeader,
		AppMain,
		AppFooter,
	},
	data() {
		return {
			genreToSearch: "All",
			genresArr: [],
		}
	},
	methods : {
		// save child variable in parent data
		filteredDiscsArr(chosenGenre) {
			this.genreToSearch = chosenGenre
		},
		getGenresArr(allGenres) {
			this.genresArr = allGenres;
		}
	}
}
</script>

<style lang="scss">
// google fonts import
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
// GENERAL RULES
	* {
		padding: 0;
		margin: 0;
		box-sizing: border-box;
	}
	
	#app {
		font-family: 'Roboto', Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}
</style>
