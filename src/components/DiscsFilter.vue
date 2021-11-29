<template>
    <div class="filter">
        <select>
            <option selected value="All">All</option>
            <option value="Rock"> Rock </option>
            <option value="Pop"> Pop </option>
            <option value="Metal"> Metal </option>
            <option value="Jazz"> Jazz </option>
        </select>
    </div>

</template>

<script>
export default {
    name: 'DiscsFilter',
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

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