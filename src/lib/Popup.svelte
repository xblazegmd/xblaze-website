<script lang="ts">
    import { fade, scale } from "svelte/transition";
    import { backOut } from "svelte/easing";
    import { onMount } from "svelte";

    let { children, width, height, flag = $bindable() } = $props();

    onMount(() => {
        const handleKeyEvent = (e: KeyboardEvent) => {
            if (e.key === "Escape") flag = false;
        };

        window.addEventListener("keydown", handleKeyEvent);
        return () => window.removeEventListener("keydown", handleKeyEvent);
    });
</script>

{#if flag}
    <div class="center popup-container" in:fade={{ duration: 75 }}>
        <div class="popup" style="width: {width}vh; height: {height}vh;" in:scale={{ duration:250, easing: backOut }}>
            {@render children()}
        </div>
    </div>
{/if}

<style>
    .popup {
        position: relative;
        padding: 1vh 3vh;
        border-width: 3.5vh;
        border-style: solid;
        border-radius: 3vh;
        background-color: #001931;
        background-clip: padding-box;
        border-image: url("$lib/assets/popup.png") 10% stretch;
        border-image-slice: 65;
        overflow: hidden;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
    }

    .popup-container {
        position: fixed;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
        background-color: rgba(0, 0, 0, 0.4);
        height: 100vh;
        z-index: 10000;
    }
</style>