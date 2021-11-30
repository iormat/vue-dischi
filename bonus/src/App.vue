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
		filteredDiscsArr(userChosenGenre) {
			this.genreToSearch = userChosenGenre
		},
		// fill genres array with child info
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

:root{
	--clr-txt-primary: #fff;
	--clr-txt-secondary: #79756F;
	--clr-primary-500: #303A45;
	--clr-primary-800: #212D3A;
}
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

	h1, h2, h3, select {
		color: var(--clr-txt-primary);
	}
	p, span {
		color: var(--clr-txt-secondary);
	}
</style>
