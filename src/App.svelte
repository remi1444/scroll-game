<script>
        import svelteLogo from "./assets/svelte.svg";
        import Game from "./lib/Game.svelte";
        import Screen from "./lib/Screen.svelte";
        let top = 0;
        let left = 0;
        let right = 0;
        let bottom = 0;

        let screenContainer;
        let ballSize = 40; // Size of the ball (width and height)

        function checkBounds() {
                const containerBounds = screenContainer.getBoundingClientRect();
          

                const rightLimit = containerBounds.width - ballSize;
                const bottomLimit = containerBounds.height - ballSize;
                right = containerBounds.right;
                bottom = containerBounds.bottom;
                // Check if the ball has reached the edges
                if (left <= 0 || top <= 0 || left >= rightLimit || top >= bottomLimit) {
                        // console.log("Reached boundary!");
                        return true; // Early return if it has reached any edge
                }
                console.log("Still within bounds.");
                return false;
        }
</script>

<main class="main">
        <Screen bind:top bind:left bind:screenContainer />
       
        <Game bind:top bind:left {checkBounds} bind:bottom  bind:right />
</main>

<style>
        .main {
                height: 100vh;
        }
</style>
