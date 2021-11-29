<template>
    <div v-if="!Loaded" id="loading-window">
        <div class="square blue"></div>
        <div class="square red"></div>
        <div class="square orange"></div>
        <div class="square green"></div>
    </div>
</template>

<script>
export default {
    name: 'Loader',
		data() {
			return {
				Loaded : false,
			}
		},
		mounted() {
			document.onreadystatechange = () => {
				if(document.readyState == 'complete') {
					this.Loaded = true;
				}
			}
		}
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #loading-window {
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        background-color: rgba(3, 3, 3, 0.466);
    }

    .square {
        width: 45px;
        aspect-ratio: 1;
        margin: 5px;
        &.blue {
            background-color: #8DC9E5;
            animation: left 1s infinite;
        }
        &.red {
            background-color: #D16C4E;
        }
        &.orange {
            background-color: #E6B65A;
        }
        &.green {
            background-color: #A5D387;
            animation: right 1s infinite 0.5s;
        }
    }
    @keyframes left {
        40% {
          transform: translateX(-60px);
        }
        50% {
          transform: translateX(0);
        }
    }
    @keyframes right {
        40% {
          transform: translateX(60px);
        }
        50% {
          transform: translateX(0);
        }
    }
</style>