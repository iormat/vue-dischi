<template>
    <header>
        <img src="@/assets/spotify-logo.png" alt="spotify logo">
        <div class="filter">
            <select v-model="selected" @change="$emit('getResults', selected)">
                <option selected value="All">All</option>
                <option value="Rock"> Rock </option>
                <option value="Pop"> Pop </option>
                <option value="Metal"> Metal </option>
                <option value="Jazz"> Jazz </option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    name: 'AppHeader',
    data() {
        return {
            selected: "All",
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    header {
        height: 80px;
        padding: 0 30px;
        background-color: #303A45;
        display: flex;
        justify-content: space-between;
        align-items: center;
        & img {
            height: 80%;
        }
    }
    .filter {
        display: flex;
        justify-content: center;
        margin: 2rem 0;
    }

    select {
        font-size: 1rem;
        width: 20ch;
        padding: .25em .5em;
        background-color: inherit;
        color: #fff;
        border: 2px solid;
        option {
            background-color: #212D3A;
        }
    }
</style>
