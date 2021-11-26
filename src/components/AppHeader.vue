<template>
    <header>
        <img src="@/assets/spotify-logo.png" alt="spotify logo">
    </header>
</template>

<script>
export default {
  name: 'AppHeader',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    header {
        height: 80px;
        padding: 0 30px;
        background-color: #303A45;
        display: flex;
        align-items: center;
        & img {
            height: 80%;
        }
    }

</style>
