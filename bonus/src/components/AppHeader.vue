<template>
    <header>
        <img src="@/assets/spotify-logo.png" alt="spotify logo">
        <div class="filter">
            <select v-model="userChosenGenre" @change="$emit('getResults', userChosenGenre)">
                <option value="All">All</option>
                <option v-for="genre, i in genres" :key="i" :value="genre"> {{genre}} </option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    name: 'AppHeader',
    data() {
        return {
            userChosenGenre: "All",
        }
    },
    props: {
        // return genres to parent(App)
        genres: Array,
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    header {
        height: 60px;
        padding: 0 30px;
        background-color: var(--clr-primary-500);
        display: flex;
        justify-content: space-between;
        align-items: center;
        & img {
            height: 70%;
        }
    }

    select {
        font-size: .9rem;
        width: 20ch;
        padding: .25em .5em;
        background-color: var(--clr-primary-800);
        border: 1px solid;
        cursor: pointer;
        option {
            outline-style: none;
        }        
    }
</style>
