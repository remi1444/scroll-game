<script>
        import { ArrowDown, ArrowLeft, ArrowRight, ArrowUp } from "lucide-svelte";

        export let top = 0;
        export let left = 0;
        export let checkBounds;
        export let right = 0;
        export let bottom = 0;
</script>

<section class="button_container">
        <div class="top_bottom">
                <button
                        class=""
                        on:click={() => {
                                if (top <= 0) {
                                        return;
                                }
                                top = top - 40;
                                checkBounds();
                        }}
                >
                        <ArrowUp />
                </button>
                <button
                        class=""
                        on:click={() => {
                                checkBounds();
                                if (top + 40 >= bottom) {
                                        // Check if the next increment will exceed the boundary
                                        top = bottom - 40; // Snap to the limit
                                } else {
                                        top += 40; // Increment as normal
                                }

                                console.log({ bottom, top });

                                console.log({ bottom, top });
                        }}><ArrowDown /></button
                >
        </div>
        <div class="right_left">
                <button
                        class=""
                        on:click={() => {
                                if (left <= 0) {
                                        return;
                                }
                                left = left - 40;

                                checkBounds();
                        }}><ArrowLeft /></button
                >
                <button
                        class=""
                        on:click={() => {
                                if (left + 40 >= right) {
                                        left = right - 40;
                                } else {
                                        left += 40;
                                }

                                checkBounds();
                        }}><ArrowRight /></button
                >
        </div>
</section>

<style>
        .button_container {
                width: 200px;
                height: 200px;
                background-color: rgb(247, 242, 242);
                border-radius: 4px;
                position: relative;
                display: flex;
                justify-content: center;
                margin: 0 auto;
        }
        .right_left {
                display: flex;
                margin: 0 auto;
                width: 85%;

                justify-content: space-between;
                align-items: center;
                height: 100%;
        }

        .right_left * {
                background: rgb(170, 168, 165);
                padding: 0.5rem;
                display: flex;
                border-radius: 50%;
        }
        .top_bottom {
                position: absolute;

                height: 85%;
                display: flex;
                top: 8%;
                left: 41%;
                flex-direction: column;
                justify-content: space-between;
                align-items: center;
        }
        .top_bottom * {
                background: rgb(170, 168, 165);
                padding: 0.5rem;
                display: flex;
                border-radius: 50%;
        }
</style>
